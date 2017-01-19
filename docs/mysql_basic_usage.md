# 基本用法

## 数据库安装

### 使用yum安装mysql5.5

1.安装repo源
```
# yum install http://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm
```

2.配置repo到mysql5.5版本

```
# vim /etc/yum.repos.d/mysql-community.repo
# yum makecache
```

3.安装mysql

```
# yum install mysql-community-server
```





## 数据库启动/停止/状态查询

### 数据库启动

```bash
$ sudo service mysqld start
```


### 数据库停止

```bash
$ sudo service mysqld stop
```


### 数据库状态查询

```bash
$ sudo service mysqld status
```


## 数据库登陆



## 数据库创建/删除

### 数据库创建

示例：创建一个名为"pdp"的数据库。

```sql
mysql> CREATE DATABASE `pdp`;
Query OK, 1 row affected (0.00 sec)
```

可以使用如下命令查询某个数据库的创建命令。

```sql
mysql> SHOW CREATE DATABASE `crashcourse`;
+-------------+------------------------------------------------------------------------+
| Database    | Create Database                                                        |
+-------------+------------------------------------------------------------------------+
| crashcourse | CREATE DATABASE `crashcourse` /*!40100 DEFAULT CHARACTER SET latin1 */ |
+-------------+------------------------------------------------------------------------+
1 row in set (0.00 sec)
```


### 数据库删除

示例：删除一个名为"pdp"的数据库。

```sql
mysql> DROP DATABASE `pdp`;
Query OK, 0 rows affected (0.04 sec)
```


## 数据表创建(C)/查询(R)/更新(U)/删除(D)

### 数据表创建(C)

示例：创建一个名为"user"的数据表。

```sql
mysql> CREATE TABLE `user` (
    -> `id` int(8) AUTO_INCREMENT,
    -> `name` varchar(20) NOT NULL DEFAULT '',
    -> `tel` varchar(16) NOT NULL DEFAULT '',
    -> PRIMARY KEY (`id`)
    -> ) DEFAULT CHARSET=utf8;
Query OK, 0 rows affected (0.15 sec)
```

参考官方文档：[数据类型](http://dev.mysql.com/doc/refman/5.6/en/data-types.html)。


### 数据表删除(D)

示例：删除一个名为"user"的数据表。

```sql
mysql> DROP TABLE user;
Query OK, 0 rows affected (0.04 sec)
```


## 表记录增加/更新/删除

### 表记录增加

不知道数据表有哪些字段的话，可以使用`DESCRIBE`命令查询。

```sql
mysql> DESCRIBE user;
+-------+-------------+------+-----+---------+----------------+
| Field | Type        | Null | Key | Default | Extra          |
+-------+-------------+------+-----+---------+----------------+
| id    | int(8)      | NO   | PRI | NULL    | auto_increment |
| name  | varchar(20) | NO   |     |         |                |
| tel   | varchar(16) | NO   |     |         |                |
+-------+-------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)
```

示例：向`user`表中插入一条记录。

```sql
mysql> INSERT INTO `user`(`name`, `tel`) VALUES('Jay', `18612345678`);
Query OK, 1 row affected (0.02 sec)
```

```sql
mysql> SELECT * FROM `user`;
+----+-------+-------------+
| id | name  | tel         |
+----+-------+-------------+
|  1 | Jay   | 18612345678 |
+----+-------+-------------+
1 rows in set (0.00 sec)
```


### 表记录更新

示例：更新`user`表中的一条记录。

```sql
mysql> UPDATE `user` SET `name` = 'jay', `tel` = '12345678900' WHERE `id` = 1;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0
```


### 表记录删除

示例：删除`c15_cd`表中的几条记录。

```sql
mysql> DELETE FROM `c15_cd` WHERE `id` = 1 OR `id` = 2;
Query OK, 2 rows affected (0.05 sec)
```


## 数据库备份/恢复

### 数据库备份

示例：备份数据库`pdp`。

```bash
$ mysqldump pdp -uroot -p > php.sql
Enter password: 
```







