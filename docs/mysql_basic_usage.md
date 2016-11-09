# 基本用法

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

说明：不知道数据表有哪些字段的话，可以使用`DESCRIBE`命令查询。

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


### 表记录删除


## 数据库备份/恢复








