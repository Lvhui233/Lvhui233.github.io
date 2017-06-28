---
layout:     post
title:      "mysql 多表查询"
subtitle:   "MySQL multi-table query"
date:       2017-06-24 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - MySQL
---


## 笛卡尔积

```
select * from stu,team;
```

## 表关联

### 笛卡尔积表关联

通过在笛卡尔积后面加上限制条件来达到关联效果

```
select * from stu,team where stu.uid=team.uid;
```

### 内关联

```
select * from stu inner join team on stu.uid=team.uid;
//可以不写inner
select * from stu join team on stu.uid=team.uid;
```

### 三张表关联

```
select * from stu join middle on stu.uid=middle.uid join team on middle.sid=team.sid;
```

### 左关联与右关联

以一侧的表为主,即显示该表的所有数据,即使没有所关联的数据

```
select * from stu left join team on stu.uid=team.uid;
select * from stu right join team on stu.uid=team.uid;
```

### 自关联

自关联时必须起别名

```
select * from stu as s1 join stu as s2 on s1.uid=s2.uid where s1.name='liming';
```