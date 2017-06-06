---
layout:     post
title:      "PHP运算符和函数"
subtitle:   "PHP operator and function"
date:       2017-05-26 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - PHP
---

## 运算符

### 比较运算符

- 不等于 `$a!=$b`
- 不等于 `$a<>$b`

## 流程控制

### switch-case

php中switch可以判断范围

```
switch($num){
	case $num<=5:
		echo 'true';
		break;
	case $num>5:
		echo 'false';
		break;
}
```

## 函数

### 函数内外变量作用域

函数内外空间是相对独立的，在函数外部声明的变量无法在函数外部调用，在函数外部声明的变量也无法在函数内部调用。

#### 函数外部调用函数内部变量

可以将变量作为返回值，在函数被调用时可以接收到返还值，如果函数中没有使用`return`返回值时，则函数的返回值为`null`。

```
<?php
function run(){
	$a = 'hello';
	return $a;
}
$a = run();
echo $a;
?>
```

#### 函数内部调用外部变量

函数内可以使用`global`将外部变量引入

```
<?php
$a = 'hello';
function run(){
	global $a;
	echo $a;
}
run();
?>
```

还可以使用全局数组`$GLOBALS`调用全局变量

```
<?php
$a = 'hello';
function run(){
	$GLOBALS('a');
	echo $a;
}
run();
?>
```
### 函数检测

检测函数是否定义`function_exists()`

检测a这个函数是否被定义

`var_dump(function_exists('a'));`

### 参数的传递

按值传递参数`function run($a){};`

按址传递参数`function run(&$a){};`

### 默认参数值

调用参数时，若没有传入参数，将使用参数的默认值，有默认值的参数必须写在其他没有默认值参数的后面

### 变量函数

php支持变量函数，如果一个变量后面有括号，会寻找与变量值同名的函数。但是变量函数不能用于语言结构，如echo(),print(),unset()

```
<?php
function a(){
	echo 'hello';
}
$x = 'a';
$x();  //将会执行函数
?>
```

### 静态变量

静态变量只在函数第一次调用时声明，用`static`关键字声明

```
function run(){
	static $x = 1;
	$x++；
	echo $x;
}
```
![](http://lvhui233.github.io/img/jingtaibianliang.png)

### 递归函数

在函数内部再次调用自身函数，递归函数必须有结束的时刻

```
递归的典型利用，计算阶乘
<?php
function jiecheng($x){
    if($x==1){
        return 1;
    }
    return $x*jiecheng($x-1);
}
echo jiecheng(5);
?>
```
