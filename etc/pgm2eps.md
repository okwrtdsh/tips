# pgm to eps on ubuntu
```shell
sudo apt-get install imagemagick
convert hoge.pgm hoge.eps
mogrify -format eps *.pgm
```
