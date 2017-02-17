# 基本用法

## 安装、启动和退出

### 使用yum安装

```
# yum install redis
```

安装成功后，Redis的可执行文件及相关配置所在位置：

|名称               |路径                                   |
|-------------------|---------------------------------------|
|服务端可执行文件   |/usr/bin/redis-server                  |
|客户端可执行文件   |/usr/bin/redis-cli                     |
|配置文件           |/etc/redis.conf                        |


### 启动redis并且在后台运行

```bash
$ nohup redis-server &
```
```bash
$ netstat -tunlp | grep redis
tcp        0      0 0.0.0.0:6379            0.0.0.0:*               LISTEN      16716/redis-server  
tcp6       0      0 :::6379                 :::*                    LISTEN      16716/redis-server
```

说明：默认的端口号为6379，默认的配置文件为/etc/redis.conf。


### 启动redis并且在后台运行(指定端口号)

```bash
$ nohup redis-server --port 5160 &
```
```bash
$ netstat -tunlp | grep redis     
tcp        0      0 0.0.0.0:5160            0.0.0.0:*               LISTEN      16988/redis-server  
tcp6       0      0 :::5160                 :::*                    LISTEN      16988/redis-server  
```


### 退出redis

```bash
$ redis-cli shutdown
```


### 退出redis(指定端口号)

```bash
$ redis-cli -p 5160 shutdown
```


## 数据结构 string

### 增加 set mset

语法：`SET key value`

示例：

```bash
$ redis-cli 
127.0.0.1:6379> set foo bar
OK
127.0.0.1:6379> get foo
"bar"
```

语法：`MSET key value [key value ...]`

示例：

```bash
127.0.0.1:6379> mset apple red banana yellow
OK
127.0.0.1:6379> mget apple banana
1) "red"
2) "yellow"
```


### 删除 del


### 修改 set mset (与增加操作相同，实为覆盖)


### 查询 get mget





## 数据结构 hash



## 数据结构 list


## 数据结构 set


## 数据结构 sorted set





