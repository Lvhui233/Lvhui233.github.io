---
layout:     post
title:      "mysql 时间与日期"
subtitle:   "MySQL time and date"
date:       2014-06-22 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - MySQL
---


## 将数据设置成日期类型

```
create table stu(sid smallint unsigned primary key auto_increment,birth date);
```

## 插入日期类数据

```
insert into stu set birth='1993/05/15';
```

## 日期相关函数

### 查询当前日期

```
select curdate();
```

### 查询当前时间

```
select curtime();
```

### 获得当前的日期和时间

```
select now();
```

### 获得日期的年份

```
select year('19920627');
```

## 查询1995后的数据

```
select * from stu where year(birth)>1995;
```


