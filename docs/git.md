# Git

## 分支 branch

### 查看分支

#### 示例：查看项目的所有分支名称

```
$ git branch
* master
```

标记星号(`*`)的分支为当前的工作分支。


### 创建分支

#### 示例：创建开发分支dev

```
$ git branch dev
$ git branch
  dev
* master
```


### 切换分支

#### 示例：切换到已经创建的dev分支

```
$ git checkout dev
Switched to branch 'dev'
```


#### 示例：创建并切换到新的dev分支

```
$ git checkout -b dev
Switched to a new branch 'dev'
```

如果分支已经存在，则会提示如下错误：
```
$ git checkout -b dev
fatal: A branch named 'dev' already exists.
```


### 提交分支代码

#### 示例：提交代码到dev分支

```
$ git add .
$ git commit -m 'add index.php'
$ git push -u origin dev
```


### 删除分支

<font color="red">删除分支包括删除本地分支和远程分支，删除本地分支或者远程分支均不会对另一个有影响。</font>

### 示例：删除本地分支dev

```
$ git branch -d dev
```

### 示例：删除远程分支dev

```
$ git push origin :dev
```


### 同步代码

#### 示例：将主干代码同步到dev分支

```
$ git checkout dev
$ git merge master
```

#### 示例：将dev分支代码同步到主干

```
$ git checkout master
$ git merge dev
```


## 标签 tag 

<font color="red">
说明：标签是打在分支的提交节点上的，打标签之前需要先切换到目标分支。
</font>

### 创建标签

#### 示例：

```
$ git tag 1.0 -m "Original version of php-5.6.30"
```


### 推送标签

#### 示例：推送1.0本地标签到远程

```
$ git push origin 1.0
```


#### 示例：推送所有本地标签到远程

```
$ git push origin --tags
```


### 删除标签

#### 示例：删除本地标签

```
$ git tag -d v1.0
```

说明：删除本地标签不会影响远程标签，删除本地标签后不要忘了删除掉对应的远程标签。


#### 示例：删除远程标签

```
$ git push origin :refs/tags/v0.9
```

说明：删除远程标签不会影响本地标签，删除远程标签后不要忘了删除掉对应的本地标签。


### 查看标签

#### 示例：查看所有的标签名称

```
$ git tag
1.0
```


#### 示例：查看某个标签的具体信息

```
$ git show 1.0
```


## FAQ

### Q: 如何撤销已经提交的commit？

假设提交了一个'解析Feed新闻分类数据的脚本'的commit，现在要将其撤销。步骤如下：

1.执行'git log'查找到该次提交之前的一次提交的commit-id，这里是'6ab6e463d29f1dab136d764368613683f023d852'。

```
$ git log
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
$ git reset --hard 6ab6e463d29f1dab136d764368613683f023d852
HEAD is now at 6ab6e46 fix bugs
$ git status
On branch tovega
Your branch is up-to-date with 'origin/tovega'.
```

<font color="red">
说明：</br>
i.使用--hard撤销之后本地的修改会被丢弃，需要先备份一下修改的数据。</br>
ii.使用--soft撤销之后本地的修改会被保留。
</font>

3.执行'git push'重新提交。

如果只commit到了本地仓库，执行：

```
$ git push -u origin tovega
```

如果commit到了远端仓库，执行：

```
$ git push -u origin tovega --force
```

4.再次执行'git log'和'git status'确认已回退成功。

```
$ git log
commit 6ab6e463d29f1dab136d764368613683f023d852
Date:   Tue Feb 7 22:07:24 2017 +0800

    fix bugs
    
    Change-Id: I8ca004a233b900e1f7a2c6c49dfd47d4525ff802
$ git status
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


### Q: 如何将fork源的代码同步到自己的repo？

以enrich的分支new-case为例：

```
git remote add upstream ssh://g@gitlab.baidu.com:8022/wuxing02/enrich.git
git pull upstream new-case
git push origin new-case
```

参考：[https://segmentfault.com/q/1010000002590371](https://segmentfault.com/q/1010000002590371)。

