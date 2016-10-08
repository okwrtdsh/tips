# テンプレートでどうしてもenumerateなどを使いたいとき
できるだけ避けるべき

```python
from django import template

register = template.Library()


@register.filter(is_safe=False)
def to_range(value):
    try:
        value = int(value)
    except ValueError:
        value = 0
    return range(value)


@register.filter(is_safe=False)
def to_enumerate(value):
    return enumerate(value)


@register.filter(is_safe=False)
def to_generator(value):
    return (v for v in value)


@register.filter(is_safe=False)
def to_split(value, arg):
    try:
        if arg:
            return value.split(arg)
        else:
            return value.split()
    except:
        return ''


@register.filter(is_safe=False)
def get_collection(value, arg):
    try:
        arg = int(arg)
    except ValueError:
        return ''
    try:
        return value[arg]
    except:
        return ''
```
