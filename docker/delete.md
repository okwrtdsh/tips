# 停止しているコンテナの削除
```
docker rm `docker ps -a -q`
```

# REPOSITORYが`<none>`のイメージの削除
```
docker rmi $(docker images | awk '/^<none>/ { print $3 }')
```
