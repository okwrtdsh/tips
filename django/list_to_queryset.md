# QuerySetにModelObjectを追加する

```python
>>> q = SomeModel.objects.none()
>>> q._result_cache = [a1, a2]
>>> q
[<SomeModel: SomeModel object>, <SomeModel: SomeModel object>]
>>> type(q)
<class 'django.db.models.query.QuerySet'>
>>> 
```
