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


## 数据结构 keys (generic)

### 命令汇总

|类别       |命令           |含义                               |
|-----------|---------------|-----------------------------------|
|删除       |del            |删除一个或多个key                  |
|查询       |exists         |查询key是否存在                    |
|           |type           |查询key的类型                      |


## 数据结构 string

|类别       |命令           |含义                               |
|-----------|---------------|-----------------------------------|
|增加       |set            |设置key的value值(字符串)           |
|           |mset           |设置一个或多个key的value值(字符串) |
|查询       |get            |查询key的value值(字符串)           |
|           |mget           |查询一个或多个key的value值         |
|           |strlen         |查询一个key的value值的长度         |

### 增加 set

#### 语法：

`SET key value`

#### 示例：

```bash
$ redis-cli 
127.0.0.1:6379> set foo bar
OK
127.0.0.1:6379> get foo
"bar"
```


### 增加 mset

#### 语法：

`MSET key value [key value ...]`

#### 示例：

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

数据格式：key field value [field value ...]

### 命令汇总

|类别       |命令           |含义                                 |
|-----------|---------------|-------------------------------------|
|增加       |hset           |设置hash里某一个field的value值       |
|           |hmset          |设置hash里某一个或多个field的value值 |
|删除       |hdel           |删除hash里某一个或多个field          |
|查询       |hkeys          |查询hash里所有field的名称            |
|           |hget           |查询hash里某一个field的value值       |
|           |hmget          |查询hash里某一个或多个field的value值 |
|           |hgetall        |查询hash里所有的field名称和value值   |
|           |hlen           |查询hash里所有field的数量            |
|           |hvals          |查询hash里所有value的值              |
|           |hexists        |查询hash里是否存在指定的field        |


## 数据结构 list


## 数据结构 set


## 数据结构 sorted set

数据格式：key score member [score member ...]

|类别       |命令               |含义                                   |
|-----------|-------------------|---------------------------------------|
|增加       |zadd               |设置zset里某一个或多个member(带score)  |
|删除       |zrem               |删除zset里某一个或多个member(指定member值删除)|
|查询       |zcard              |查询zset里member的数量                 |
|           |zcount             |查询zset里某个分数范围内member的数量   |
|           |zrange             |查询zset里某个下标范围内的member       |
|           |zrevrange          |查询zset里某个下标范围内的member(倒序) |
|           |zrangebyscore      |查询zset里某个分数范围内的member       |
|           |zrevrangebyscore   |查询zset里某个分数范围内的member(倒序) |

### 增加 zadd

#### 语法：

`zadd key score value [score value [...]]`

#### 说明：

score: float

#### 示例：

```bash
127.0.0.1:6379> zadd foo 2.0 bar1 3.0 bar2
(integer) 2
```


### 删除 zrem/zdelete

#### 语法：

`zrem key value`


#### 示例：

```bash
127.0.0.1:6379> zrem foo bar1
(integer) 1
```


#### 示例：redis2.8.19版本不支持zdelete命令

```bash
127.0.0.1:6379> zdelete foo bar2
(error) ERR unknown command 'zdelete'
```


### 查询 zrange

#### 

语法：`zrange key start stop [withscores]`


#### 说明：

该方法只能查询到value，不能查询score。

start: int, 起始位置, 前编号从0开始，后编号从-1开始, 可以取值-inf

stop: int, 结束为止，前编号从0开始，后编号从-1开始, 可以取值+inf


#### 示例：

```bash
127.0.0.1:6379> zrange foo 0 -1
1) "bar1"
2) "bar2"
```


### 查询 zrevrange

#### 

语法：`zrevrange key start stop [withscores]`


#### 说明：

<font color="red">
zrevrange是zrange的倒序版本。
</font>

该方法只能查询到value，不能查询score。

start: int, 起始位置, 前编号从0开始，后编号从-1开始, 可以取值-inf

stop: int, 结束为止，前编号从0开始，后编号从-1开始, 可以取值+inf


#### 示例：

```bash
127.0.0.1:6379> zrevrange foo 0 -1
1) "bar2"
2) "bar1"
```


### 查询 zscore

#### 

语法：`zscore key value`


#### 示例：查询'bar2'这个value对应的score

```bash
127.0.0.1:6379> zscore foo bar2
"3"
```


## 分类命令 @server

|类别       |命令               |含义                                   |
|-----------|-------------------|---------------------------------------|
|删除       |flushall           |删除所有的key                          |

