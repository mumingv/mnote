# Git

## FAQ

### Q: 如何将本地的目录提交到一个新建的仓库？

以test仓库为例：

```
echo "# test" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/mumingv/test.git
git push -u origin master
```


