# vim最短マッチは?ではない

`\{-}`が最短マッチ

```
:%s/\({{ MEDIA_URL }}\)\(.\{-}\)\("\|'\)/{% static "\2" %}\3/g
```