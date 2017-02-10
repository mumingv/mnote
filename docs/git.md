# Git

## FAQ

### Q: 如何撤销已经提交的commit？

<font color="red">
注：撤销之后本地的修改会被丢弃，需要先备份一下修改的数据。
</font>

假设提交了一个'解析Feed新闻分类数据的脚本'的commit，现在要将其撤销。步骤如下：

1.执行'git log'查找到该次提交之前的一次提交的commit-id，这里是'6ab6e463d29f1dab136d764368613683f023d852'。

```
[audio]$ git log
commit 0197bf0aaac5cb2182a46223f4130761ecc9844b
Author: Jay Yin <mumingv@163.com>
Date:   Fri Feb 10 14:55:55 2017 +0800

    解析Feed新闻分类数据的脚本
    
    Change-Id: I40b54da24812d666f63c00794ba5e64710511841

commit 6ab6e463d29f1dab136d764368613683f023d852
Author: hanjingjing01 <hanjingjing01@baidu.com>
Date:   Tue Feb 7 22:07:24 2017 +0800

    fix bugs
    
    Change-Id: I8ca004a233b900e1f7a2c6c49dfd47d4525ff802
```

2.执行'git reset'将本地代码库恢复到前一次提交。

```
[audio]$ git reset --hard 6ab6e463d29f1dab136d764368613683f023d852
HEAD is now at 6ab6e46 fix bugs
[audio]$ git status
On branch tovega
Your branch is up-to-date with 'origin/tovega'.
```

3.再次执行'git log'和'git status'确认已回退成功。

```
[audio]$ git log
commit 6ab6e463d29f1dab136d764368613683f023d852
Author: hanjingjing01 <hanjingjing01@baidu.com>
Date:   Tue Feb 7 22:07:24 2017 +0800

    fix bugs
    
    Change-Id: I8ca004a233b900e1f7a2c6c49dfd47d4525ff802
[audio]$ git status
On branch tovega
Your branch is up-to-date with 'origin/tovega'.
```


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


