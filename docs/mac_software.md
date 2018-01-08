# 软件列表

## 软件列表

### 设计

###### 

|名称		|说明		|
|-----------|-----------|
|Sketch		|矢量绘图		|
|MindManager|思维导图		|
|iThoughtsX |思维导图		|
|EdrawMax	|流程图		|


### 调试

###### 

|名称		|说明		|
|-----------|-----------|
|Charles	|抓包工具		|
|Fiddler	|抓包工具		|
|Whistle	|抓包工具		|


## Homebrew

### 功能

Homebrew是Mac系统的软件包管理工具。使用brew安装的软件都在`/usr/local/Cellar`目录下。


### 参考资料

官网地址：https://brew.sh/index_zh-cn.html

[Homebrew总结](http://www.jianshu.com/p/8ad7056b243f)


### 常用命令

```
brew install xxx // 安装软件
brew uninstall xxx // 卸载软件
brew search // 查找能够安装的软件
brew list // 查看已安装的软件
brew update  // 升级brew自身
brew upgrade xxx  // 升级软件 
brew options xxx  // 查看安装选项
brew unlink xxx  // 删除命令快捷方式（多版本时切换版本使用）
brew link xxx  // 增加命令快捷方式（多版本时切换版本使用）
brew tap homebrew/homebrew-php // 安装软件源
brew untap homebrew/homebrew-php // 删除软件源
```


### 示例

```bash
$ brew install wget
```


## Apache

### 安装

Mac自带apache，这里不再另行安装。


### 常用命令

```
sudo apachectl start  // 启动
sudo apachectl restart  // 重启
sudo apachectl stop  // 关闭
```


### FAQ

#### Q：如何通过 http://localhost/ 访问Sites目录，而不是通过 http://localhost/~muming/ 访问？

修改配置文件

```
sudo /etc/apache2/httpd.conf
```

增加如下配置

```
DocumentRoot /Users/muming/Sites
<Directory /Users/muming/Sites>
    Options Indexes MultiViews
    # apache 2.2
    # AllowOverride All
    # Order allow,deny
    # Allow from 127.0.0.1

    # apache 2.4
    Require local
</Directory>
```

重启apache生效

```
sudo apachectl restart
```


## Charles

### 安装


### 参考资料

安装参考：http://www.jianshu.com/p/1c1023036a75


## Fiddler

### 参考资料

博客：https://imququ.com/post/use-fiddler-on-macos.html

## Whistle

### 参考资料

官方网站：https://github.com/avwo/whistle


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


