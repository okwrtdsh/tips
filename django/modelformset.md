# modelformsetを使うときに気を付けること
```python
formset_class = modelformset_factory(Model, form=ModelForm)

if request.method == "POST":
    formset = formset_class(request.POST)
else:
    formset = formset_class()
context = {"formset": formset}
```

```html
{{ formset.management_form }}
{% for form in formset %}
  {{ form }}
  {{ form.id }}{# 要注意 #}
{% endfor %}
```
