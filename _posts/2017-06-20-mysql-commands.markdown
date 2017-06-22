---
layout:     post
title:      "mysql 常用命令"
subtitle:   "MySQL Common commands"
date:       2017-06-20 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - MySQL
---


## 常用命令


### 显示当前所有数据 

```
show databases;
```

### 创建一个数据库 

```
create database 数据库名;
```

### 创建数据库并设置编码 

```
create database one charset utf8;
```

### 删除数据库 

```
drop database 数据库名;
```

### 进入数据库(使用数据库) 

```
use 数据库名
```

### 创建users数据表，设置表里面的字段 

```
create table users(aid int unsigned primary key auto_increment,name char(20),password char(32));
```

### 查看users表结构

```
desc users
```

### 插入数据 

```
insert into 表名 set name='lucy',password='123';
```

### 查看users表中所有数据 

```
select * from users;
```

### 查看数据库中的所有表 

```
show tables;
```

### 删除表 

```
drop table 表名;
```

### 删除数据 

```
delete from 表名 where aid=1;
```

### 更新数据 

```
update 表名 set name='nick',password='daad' where aid=1;
```

### 删除数据库，并且判断是否存在 

```
drop database if exists abc;
```

### 查询art表中所有content字段的数据 

```
select content from art;
```

### decimal第一个参数表示数字的位数，第二个参数表示小数占用的位数

```
create table shop(title char(30),price decimal(10,3));
```

### 创建shop数据表，同时设置title字段数字长度是6位，不足的用前导零填充

```
create table shop(title smallint(6) zerofill);
```

### 枚举(类似单选和复选),未在字段中指定的数据无法存入

```
create table student(name char(20),sex enum('male','female'),hobby set('soccer','tennis',bsaketball));
```

### 约束键

设置某一字段不能重复

```
create table fruit(fname char(30) unique,price decimal(7,3));
```

### 搜索

```
//只能搜索完整数据(不常用)
select * from student where find_in_set ('soccer',hobby);
//更广泛的搜索
select * from student where hobby like '%soc%';
```

### 查看数据表的原始创建信息

```
show create table 表名;
```

### 清空表，同时重置自增字段

```
truncate 表名;
```

### 复制表结构

```
create table ab like abc;
```

### 将abc表中的所有数据都复制到ab表中

需要两个表的·结构相同

```
insert into ab select * from abc;
```

### 同时复制结构和内容

主键结构不会复制

```
create table ab select * from abc;
```

### 同时插入多条数据

```
insert into student (name,sex,hobby) values ('liming','male','soccer,tennis'),('zhaoxia','male','basketball');
```

### 别名

别名不能用在where中

```
select name,sex as s from student;
```

### and or

```
select * from student where name='liming' and sex='male';
select * from student where name='zhaoxia' or sex='male';
//搜索所有数据
select * from student where sex='male' or true;
```

### 连接

将输出连接后的结果

```
select concat(name,'-',hobby) from student;
```

### 对数据筛选验证

```
//age>22如果是真就是1,,假就是0
select name,age,age>22 from student;
//自定义真假所显示的值
select name,if(age>22,'true','false') from student;
```

### 查询student表中name字段是null的数据

```
select * from student where name is null;
//查询非null数据
select * from student where name is not null;
```

### 查询时排序

```
//由大到小
select * from student order by age desc;
//由小到大
select * from student order by age asc;
//先用age排序,若有相同的再用sid排序
select * from student order by age desc,sid desc;
```

### 截取查询结果

```
//截取前五条
select * from student limit 5;
//从第3条开始，截取4条
select * from student limit 2,4;
```

### 随机抽取数据

```
//随机抽3条数据
select * from student order by rand() limit 3;
//随机抽4条年龄大于20岁的数据
select * from student where age>20 order by rand() limit 4;
```

### 查询age在20到23之间的数据

```
select * from stu where age between 20 and 23;
```

### 查询age是23或31的数据

```
select * from stu where age in(23,31);
```

### 查询stu表中name字段中含有guo的数据

```
select * from stu where name like '%guo%';
```

### 查询stu表中name字段中以guo开头的数据

```
select * from stu where name like 'guo%';
```

### 查询stu表中name字段以cheng结尾的数据

```
select * from stu where name like '%cheng';
```

### 查询stu表中name字段是li?的数据

下划线代表任意的一个非空字符

```
select * from stu where name like 'li_';
```

### 查询stu表中sid和name字段，截取name字段的前2个字符

```
select sid,left(name,2) fro, stu;
```

### 替换数据

```
//若不设置主键,追加到最后
replace into stu (name,age) value ('liming',25);
//设置主键,将替换数据
replace into stu (sid,name,age) value (18,'liming',25);
```

### 删除age小于18的数据

```
delete from stu where age<18;
```

### 获得stu表中有多少条数据

```
select count(*) from stu;
```

### 查看最大最小age

```
select max(age) from stu;
select min(age) from stu;
```

### 计算age字段总和

```
select sum(age) from stu;
```

### 计算age字段的平均数

```
select avg(age) from stu;
```

### 依据sex字段分组

```
select * from stu group by sex;
```

### 分组后筛选

```
select * from stu group by sex having sex='male';
```