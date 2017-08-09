# 软件列表

## Homebrew

### 功能

Homebrew是Mac系统的软件包管理工具。使用brew安装的软件都在`/usr/local/Cellar`目录下。


### 参考资料

官网地址：https://brew.sh/index_zh-cn.html


### 示例

```bash
$ brew install wget
```


## MongoDB

### 安装&配置

#### 安装

```
$ brew install mongodb
```

软件的安装位置：/usr/local/Cellar/mongodb

#### 创建数据存放目录

```
$ pwd
/usr/local/Cellar/mongodb
$ mkdir -p data/db
```


### 启动

`--dbpath`指定数据文件存放的位置，`--rest`表示同时启动一个Http页面服务。

```
$ mongod --dbpath=/usr/local/Cellar/mongodb/data/db --rest
```

在页面中输入`http://localhost:28017`查看MongoDB状态。


