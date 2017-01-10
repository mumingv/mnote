# FAQ

## 如何安装Redis？

### 使用yum安装

```
# yum install redis
```


## Redis可执行文件及相关配置在什么位置？

|名称               |路径                                   |
|-------------------|---------------------------------------|
|服务端可执行文件   |/usr/bin/redis-server                  |
|客户端可执行文件   |/usr/bin/redis-cli                     |
|配置文件           |/etc/redis.conf                        |


## Redis被攻击了，如何组织Redis被外网访问？

Redis被攻击，出现如下名为"crackit"的key。

```
127.0.0.1:6379> KEYS *
1) "crackit"
2) "foo"
```

### 解决方法

修改配置`/etc/redis.conf`，仅允许本机访问。

```
bind 127.0.0.1
```

使用非root账号，重启redis-server，并指定配置。

```
$ nohup redis-server /etc/redis.conf &
```


