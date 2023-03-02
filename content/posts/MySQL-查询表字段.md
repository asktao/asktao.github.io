---
title: "MySQL 查询表字段"
date: "2021-10-07T14:56:04+08:00"
tags: [MySQL]
---

查询数据库中某个字段的使用情况，可以借助 MySQL 的 information_schema

例：查询 user_name 的字段

```SQL
SELECT * FROM `information_schema`.`columns` WHERE `column_name` = 'user_name';
```

亦支持 like

```SQL
SELECT * FROM `information_schema`.`columns` WHERE `column_name` LIKE '%user_name%';
```


