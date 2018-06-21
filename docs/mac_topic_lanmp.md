# LNMP环境搭建

## Nginx

### 安装

```
brew install nginx
```


### 配置文件

nginx使用的配置文件目录如下。

```
/usr/local/etc/nginx
```


### 常用操作

#### 启动

```
# nginx
```


#### 退出

```
$ nginx -s quit
```


#### 查看状态

```
$ lsof -Pni4 | grep nginx
```


## PHP

### 安装php软件源

默认情况下，使用 `home search php` 命令是查不到php安装包的，需要先安装brew源才能查到各个php版本。

```
brew tap homebrew/homebrew-php
```


### 安装多版本php

首先安装一个php版本。

```
brew install php70
```

如果需要安装多个php版本，首先需要把当前使用的版本unlink掉之后再安装新的版本。

```
brew unlink php70
brew install php72
```

如果不想通过unlink后再install的方式来切换版本，而是使用版本管理工具php-version来切换的话，需要把当前的版本给unlink掉。

```
brew unlink php72
```


### 多版本切换

安装php-version版本管理工具

```
brew install php-version
```

安装后执行如下命令，将php可执行文件路径加入PATH变量。

```
source $(brew --prefix php-version)/php-version.sh && php-version 5.6.31
```

查询版本号

```
php-version
* 5.6.31
  7.0.22
  7.2.0beta2
```

切换版本

```
php-version 7.0.22
```


### 配置文件

各php版本使用的配置文件目录如下。

```
$ ls -1 /usr/local/etc/php
5.6
7.0
7.2
```


### 常用操作

#### 启动

```
# php-fpm -D
```


#### 退出

```
$ killall php-fpm
```


#### 查看状态

```
$ lsof -Pni4 | grep php-fpm
php-fpm   4909 muming    7u  IPv4 0x42f424f650baa87f      0t0  TCP 127.0.0.1:9000 (LISTEN)
php-fpm   4910 muming    0u  IPv4 0x42f424f650baa87f      0t0  TCP 127.0.0.1:9000 (LISTEN)
php-fpm   4911 muming    0u  IPv4 0x42f424f650baa87f      0t0  TCP 127.0.0.1:9000 (LISTEN)
php-fpm   4912 muming    0u  IPv4 0x42f424f650baa87f      0t0  TCP 127.0.0.1:9000 (LISTEN)
```


## MySQL

### 安装

```
brew install mysql
```

安装成功后，系统默认创建一个没有密码的root用户。


### 使用

#### 启动

方式一（开机不自动启动）

```
mysql.server start
```

方式一（开机自动启动）

```
brew services start mysql
```


### 登陆

默认root用户没有密码，直接登陆。如果存在密码，则与阿里云相同（Mysql..6.）。

```
mysql -uroot
```


### 修改密码

#### 没有密码时设置

```
mysqladmin -uroot password '123'
```


#### 有密码时设置

```
mysqladmin -uroot -p123 password '456'
```


#### 删除密码

```
mysqladmin -uroot -p123 password '456'
```


## 配置示例




## 参考资料

[Mac下用brew搭建LNMP和LAMP开发环境](http://yansu.org/2013/12/11/lamp-in-mac.html)

[全新安装 Mac OS Sierra (10.12) 并使用 HomeBrew 安装 ZSH + MNMP (Mac + Nginx + MySQL + PHP) 开发环境](https://laravel-china.org/topics/3129/new-installation-mac-os-sierra-1012-and-use-homebrew-to-install-zsh-mnmp-mac-nginx-mysql-php-development-environment)
