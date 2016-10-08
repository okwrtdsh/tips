# ChoicesをTextInputで選択するwidget

```python
from __future__ import unicode_literals
from itertools import chain
from django.forms.widgets import Widget
from django.forms.utils import flatatt
from django.utils import formats
from django.utils.encoding import force_text
from django.utils.html import format_html
from django.utils.safestring import mark_safe

class SelectInput(Widget):
    """
    <ul style="display: table; table-layout: fixed; text-align: center; width: 100%;">
    <li value="" style="display: table-cell; vertical-align: middle;">---------</li>
    <li value="1" style="display: table-cell; vertical-align: middle;">HOGE</li>
    <li value="2" style="display: table-cell; vertical-align: middle;">FUGA</li>
    ...
    </ul>
    <input id="id_name" name="name"/>
    """

    def __init__(self, attrs=None, choices=()):
        super(SelectInput, self).__init__(attrs)
        self.choices = list(choices)

    def _format_value(self, value):
        if self.is_localized:
            return formats.localize_input(value)
        return value

    def render(self, name, value, attrs=None, choices=()):
        if value is None:
            value = ''
        final_attrs = self.build_attrs(attrs, name=name)
        if value != '':
            final_attrs['value'] = force_text(self._format_value(value))
        output = []
        options = self.render_options(choices, [value])
        if options:
            output.append(options)
        output.append(format_html('<input{}>', flatatt(final_attrs)))
        return mark_safe('\n'.join(output))

    def render_option(self, selected_choices, option_value, option_label):
        prefix = ''
        if option_value is None:
            option_value = ''
        else:
            if option_value != '':
                prefix = '%s: ' % option_value
        return format_html('<li value="{}" style="display: table-cell; vertical-align: middle;">{}{}</li>',
                           option_value,
                           prefix,
                           force_text(option_label))

    def render_options(self, choices, selected_choices):
        selected_choices = set(force_text(v) for v in selected_choices)
        output = ['<ul style="display: table; table-layout: fixed; text-align: center; width: 100%;">']
        for option_value, option_label in chain(self.choices, choices):
            output.append(self.render_option(selected_choices, option_value, option_label))
        output.append('</ul>')
        return '\n'.join(output)
```
