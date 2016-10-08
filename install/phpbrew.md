# PHPのビルド

```bash
CXX=g++ phpbrew --debug install --old 7.0.6 +default +fpm +mysql -- --enable-force-cgi-redirect --enable-fastcgi --with-libxml-dir=/usr/local/Cellar/libxml278/2.7.8 --with-mysql --with-mysqli --with-pdo-mysql --with-libedit
```

http://qiita.com/sira/items/7414d34d061d779d3561
