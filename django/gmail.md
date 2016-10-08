# Gmail

```python
EMAIL_USE_TLS = True
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_HOST_USER = 'youremail@gmail.com'  # 使用するgmailアカウント
EMAIL_HOST_PASSWORD = 'yourpassword'     # 使用するgmailアカウントのパスワード
EMAIL_PORT = 587
```

```python
$ python manage.py shell

>>> from django.core.mail import send_mail

>>> send_mail(u'タイトル',
              u'本文',
             'from@example.com',
             ['to@example.com'],   # 送信先アドレス
             fail_silently=False)
```
