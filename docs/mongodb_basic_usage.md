# 基本用法

## 安装

### Mac

#### 安装

```
$ brew install mongodb
```

软件的安装位置：/usr/local/Cellar/mongodb

### 创建数据存放目录

```
$ pwd
/usr/local/Cellar/mongodb
$ mkdir -p data/db
```

### Linux

```
$ yum install mongodb
```


## 启动

### Mac

`--dbpath`指定数据文件存放的位置，`--rest`表示同时启动一个Http页面服务。

```
$ mongod --dbpath=/usr/local/Cellar/mongodb/data/db --rest
```

在页面中输入`http://localhost:28017`查看MongoDB状态。


## 连接

### 连接MongoDB

```
$ mongo
```

### 选择／切换数据库

```
> use test
switched to db test
```


## 增加

### 创建集合

```
> use runoob
switched to db runoob
> db.createCollection("mycollection")
{ "ok" : 1 }
```


### 增加文档

#### insert

方式1:

```
> db.coll.insert({'name':'菜鸟教程','site':'www.runoob.com'})
WriteResult({ "nInserted" : 1 })
```

方式2:

```
> document = ({'name':'百度','site':'www.baidu.com'})
{ "name" : "百度", "site" : "www.baidu.com" }
> db.coll.insert(document)
WriteResult({ "nInserted" : 1 })
```


#### save

<font color="red">
说明：也可以使用save函数增加文档。如果插入的数据不带id属性，则两者效果一样；如果带id属性，则save函数会更新文档。
</font>


#### insertOne

```
> db.coll.insertOne({"a": 3})
{
	"acknowledged" : true,
	"insertedId" : ObjectId("5989be04e06d7fa45e49994b")
}
```


#### insertMany

```
> db.coll.insertMany([{"b": 3}, {'c': 4}])
{
	"acknowledged" : true,
	"insertedIds" : [
		ObjectId("5989be87e06d7fa45e49994d"),
		ObjectId("5989be87e06d7fa45e49994e")
	]
}
```


#### 

## 删除

### 删除数据库

```
> use runoob
switched to db runoob
> db.dropDatabase()
{ "dropped" : "runoob", "ok" : 1 }
```


### 删除文档

#### 删除符合某个条件的文档

```
> db.coll.find()
{ "_id" : ObjectId("5989bb96e06d7fa45e499947"), "name" : "菜鸟教程", "site" : "www.runoob.com" }
{ "_id" : ObjectId("5989bc06e06d7fa45e499948"), "name" : "百度", "site" : "www.baidu.com" }
> db.coll.remove({"name":"百度"})
WriteResult({ "nRemoved" : 1 })
> db.coll.find()
{ "_id" : ObjectId("5989bb96e06d7fa45e499947"), "name" : "菜鸟教程", "site" : "www.runoob.com" }
```


#### 删除所有文档

```
> db.collection.find()
{ "_id" : ObjectId("5989bdd0e06d7fa45e499949"), "a" : 3 }
{ "_id" : ObjectId("5989bddbe06d7fa45e49994a"), "a" : 3 }
> db.collection.remove({})
WriteResult({ "nRemoved" : 2 })
> db.collection.find()
>
```


## 修改

### 修改文档

#### update

```
> db.coll.find()
{ "_id" : ObjectId("5989bb96e06d7fa45e499947"), "name" : "菜鸟教程", "site" : "www.runoob.com" }
> db.coll.update({"name":"菜鸟教程"},{$set:{"name":"百度","site":"www.baidu.com"}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.coll.find()
{ "_id" : ObjectId("5989bb96e06d7fa45e499947"), "name" : "百度", "site" : "www.baidu.com" }
```


#### save

```
> db.coll.find()
{ "_id" : ObjectId("5989bb96e06d7fa45e499947"), "name" : "百度", "site" : "www.baidu.com" }
> db.coll.save({"_id":ObjectId("5989bb96e06d7fa45e499947"), "name":"百度TEST", "site":"www.baidutest.com"})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.coll.find()
{ "_id" : ObjectId("5989bb96e06d7fa45e499947"), "name" : "百度TEST", "site" : "www.baidutest.com" }
```


## 查询

### 查询当前操作的数据库

```
> db
test
```


### 查询所有数据库

```
> show dbs
admin  0.000GB
local  0.000GB
```


### 查询集合中的所有文档

#### find

```
> db.coll.find()
{ "_id" : ObjectId("5989bb96e06d7fa45e499947"), "name" : "菜鸟教程", "site" : "www.runoob.com" }
```


#### find.pretty

```
> db.coll.find().pretty()
{
	"_id" : ObjectId("5989bb96e06d7fa45e499947"),
	"name" : "菜鸟教程",
	"site" : "www.runoob.com"
}
```


### 按条件查询集合中的文档

#### find

```
> db.coll.find({"name":"菜鸟教程"})
{ "_id" : ObjectId("5989bb96e06d7fa45e499947"), "name" : "菜鸟教程", "site" : "www.runoob.com" }
```


#### find.pretty

```
> db.coll.find({"name":"菜鸟教程"}).pretty()
{
	"_id" : ObjectId("5989bb96e06d7fa45e499947"),
	"name" : "菜鸟教程",
	"site" : "www.runoob.com"
}
```






