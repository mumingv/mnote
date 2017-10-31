# FAQ

## Mysql搭建了两套数据库分别使用不同的端口，如何在启动第二套数据库时制定配置文件？

第一套数据库启动时，使用`--defaults-file`参数指定配置文件；第二套数据库启动时，需要使用`--defaults-extra-file`参数指定配置文件。如下所示：

```
$ ./.jumbo/bin/mysqld_safe --defaults-extra-file=/home/work/data/mysql_8307/my.cnf  --datadir=/home/work/data/mysql_8307/data &
```