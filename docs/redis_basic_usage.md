# 基本用法

## 启动和退出

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







