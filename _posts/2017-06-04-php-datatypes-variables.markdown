---
layout:     post
title:      "PHP数据类型和变量"
subtitle:   "PHP data types and variables"
date:       2017-05-25 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - PHP
---


### 什么是php

PHP: Hypertext Preprocessor 即超文本预处理的缩写

### B/S和C/S结构

B/S结构，即大家所熟知的客户机与服务器结构，大部分预算在个人pc端上进行。C/S结构是浏览器与服务器结构，大部分的运算都在服务器上进行。

### 基础

#### HTML混排

php会直接输出结束标记和下一个开始标记之间的所有代码，在需要输出大量文本时，用这种方法退出php的解析模式会更加有效

```
<?php
	if($string){
?>
	<p>hello</p>
<?php
	}else{
?>
	<p>world</p>
<?php
	}
?>
```

#### 注释

* `//`单行注释
* `/*...*/` 多行注释
* `#`脚本注释

### 数据类型

#### 布尔型

当转换成布尔值时，以下值会被认为是false
1. 布尔值false
2. 整形值0
3. 浮点值0.0
4. 空字符串
5. 字符串"0"
6. 没有成员的数组变量
7. 没有单元的对象
8. 特殊类型null
其他值都被认为是true

#### NULL

null数据类型只有一个值null，以下几种情况会被认为是null
1. 变量未被赋予任何值
2. 变量被赋值为null
3. 被unset()函数处理过后的变量

#### 取得数据类型函数

`getType();`

#### 判断数据类型函数

- `is_bool` 是否为布尔值
- `is_int`  是否为整形
- `is_float` 是否为浮点数
- `is_strd` 是否为字符串
- `is_null` 是否为bull

#### 数据类型转换

##### 自动转换

- php数据类型根据值，自动转换

##### 强制转换

- `settype($a,'integer');` 数据类型设置函数
- `intval(); floaval(); strval();` 数据类型转换函数

### 变量

#### 定义变量

以美元符$开头，变量名则是以字母或下滑线开头，后面跟上任意数量的字母、数字和下划线

#### 变量赋值

- 传值赋值 `$a = $b`
- 传址赋值 `$a = &$b`

#### 可变变量

一个变量可以作为另一个变量的变量名

```
<?php
$a = 'hello';
$$a = 'world';
echo "$a $$a"; 
echo "$a $hello";
//两个echo都输出 "hello world"
?>
```

#### 外部变量

存储表单提交的数据
`$_GET('var')`  get参数
`$_POST('var')` post参数
`$_REQUEST('var')` 可接受get与post及cookie参数

#### 常量

`define('常量名',值)` 常量名一般用大写字母

#### 系统常量

`PHP_VERSION` 显示PHP版本

`PHP_OS` 显示服务器的操作系统版本

`TRUE FALSE` 表示真假的常量

#### 变量与常量检测

检测变量是否存在
`is_set()`

删除变量
`unset()` 是一个语句，没有返回值

检测常量是否存在
`defined()`

### 变量的输出

`echo` 输出文本
`print` 输出文本

`var_dump()` 打印变量信息(详细)

`print_r()` 打印变量信息(简单)






