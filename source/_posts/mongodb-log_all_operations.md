---
title: MongoDB logging all operations
date: 2023-04-08 09:00:00
updated: 2023-04-08 09:00:00
categories:
- MongoDB
tags: 
- MongoDB
- Logging
- Optimizing
---

## You can log all operations

```bash
$ mongo
MongoDB shell version: 2.4.9
connecting to: test
> use myDb
switched to db myDb
> db.getProfilingLevel()
0
> db.setProfilingLevel(2)
{ "was" : 0, "slowms" : 1, "ok" : 1 }
> db.getProfilingLevel()
2
> db.system.profile.find( { millis : { $gte: 1 }, appName : { $exists : false }, ns : { $not : /system.profile/ } } ).sort( { ts : -1 } )

```
  
[Source: http://docs.mongodb.org/manual/reference/method/db.setProfilingLevel/](http://docs.mongodb.org/manual/reference/method/db.setProfilingLevel/)
db.setProfilingLevel(2) means "log all operations".

## How to drop the collection system.profile

* Firstly, turn off the profiling by setting its level to 0.

```bash
db.setProfilingLevel(0)
```

* Then you can simply drop the collection.
  
```bash
db.system.profile.drop()
```

* Now you are free to go and start it all over.

## How to list operations meets the criteria

```javascript
//查询指令记录。
//过滤条件：1.需耗时（millis字段)多少毫秒以上，2.appName字段不存在（可能指令来自某APP，如Studio 3T), 3.ns字符串中不包含system.profile（排除指令是system.profile相关的）。
//排序：按时间排序。
db.system.profile.find( { millis : { $gte: 1 }, appName : { $exists : false }, ns : { $not : /system.profile/ } } ).sort( { ts : -1 } )
```
