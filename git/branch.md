# 不要になったbranchを削除して、localのbranchをremoteのbranchと合わせる
```bash
git branch -r --merged develop | grep -v -e master -e develop | sed -e 's%[0-9]*: *%%' | xargs -I% git branch -d -r %
git branch --merged develop | grep -vE '^\*|master$|develop$' | sed -e 's%[0-9]*: *%%' | xargs -I % git branch -d %
```
