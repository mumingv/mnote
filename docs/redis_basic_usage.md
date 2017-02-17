# 基本用法

## 安装

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


## 启动和关闭

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


### 关闭redis

```bash
$ redis-cli shutdown
```


### 关闭redis(指定端口号)

```bash
$ redis-cli -p 5160 shutdown
```


## 登陆和退出

### 登陆本机的redis默认端口

```
$ redis-cli 
127.0.0.1:6379> 
```


### 登陆指定机器特定端口的redis

```
$ redis-cli -h 127.0.0.1 -p 6379
127.0.0.1:6379>
```


### 退出

```
127.0.0.1:6379> quit
$ 
```

说明：使用快捷键<Ctrl + D>的效果也是一样的。


## 获取帮助

### 查询可能用到的帮助命令

```
127.0.0.1:6379> help
redis-cli 2.8.19
Type: "help @<group>" to get a list of commands in <group>
      "help <command>" for help on <command>
      "help <tab>" to get a list of possible help topics
      "quit" to exit
```

说明：使用问号的效果也是一样的。

```
127.0.0.1:6379> ?
redis-cli 2.8.19
Type: "help @<group>" to get a list of commands in <group>
      "help <command>" for help on <command>
      "help <tab>" to get a list of possible help topics
      "quit" to exit
```


### 查询某种类别当中的所有命令

```
127.0.0.1:6379> help @sorted_set

  ZADD key score member [score member ...]
  summary: Add one or more members to a sorted set, or update its score if it already exists
  since: 1.2.0

  ...
```

### 查询具体的命令

```
127.0.0.1:6379> help zadd

  ZADD key score member [score member ...]
  summary: Add one or more members to a sorted set, or update its score if it already exists
  since: 1.2.0
  group: sorted_set
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

### 增加 zadd

语法：``

示例：

```bash
```

语法：``

示例：

```bash
```




