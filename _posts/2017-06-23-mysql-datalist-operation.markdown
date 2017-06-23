---
layout:     post
title:      "mysql 表操作"
subtitle:   "MySQL datalist operation"
date:       2017-06-23 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - MySQL
---


## 给表重命名

```
alter table stu rename stu2;
```

## 字段操作

### 重定义字段

```
alter table stu change age age2 tinyint unsigned;
```

### 修改字段属性

需要将字段属性写全

```
alter table stu modify sid smallint unsigned primary key auto_increment;
```

### 移动字段

被移动的字段需要指定属性

```
alter table stu modify sex enum('male','female') after age;
```

### 删除字段

```
alter table stu drop sid;
```

### 新增字段

```
alter table stu add tel char(11) default '18888888888';
```

### 为字段设置主键

```
alter table stu add primary key(sid);
```

### 删除表中主键

```
alter table stu drop primary key;
```
