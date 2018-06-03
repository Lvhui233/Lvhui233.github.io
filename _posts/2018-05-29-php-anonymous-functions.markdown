---
layout:     post
title:      "匿名函数 "
subtitle:   "closure function"
date:       2018-05-29 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - php
---

匿名函数也叫闭包函数,允许临时创建一个没有名称的临时函数,目前是通过Closure类实现的

## 从父作用域继承变量

继承父作用域中的变量需要用use关键字

### use传值赋值

函数继承的父作用域的变量值是函数定义时变量的值，而不是函数调用时变量的值

闭包函数可以作为变量的值来使用。PHP 会自动把此种表达式转换成内置类 Closure 的对象实例。把一个 closure 对象赋值给一个变量的方式与普通变量赋值的语法是一样的，最后也要加上分号：

```
$message = 'hello';
$example = function() use ($message) {
	var_dump($message);
};
$message = 'world';
$example(); 
//输出 string(5) "hello"
```

### user传址赋值

父作用域的变量改变直接影响到匿名函数

```
$message = 'hello';
$example = function() use (&$message) {
	var_dump($message);
};
$message = 'world';
$example(); 
//输出 string(5) "world"
```

### 进行常规传参

```
$message = 'world';
$example = function ($arg) use ($message) {
    var_dump($arg . ' ' . $message);
};
$example("hello"); 
//输出 string(11) "hello world"
```

## 实现闭包

### 在函数内部调用匿名函数

```
function closureFun(){
	$func = function($str){
		echo $str;
	};
	$func('hello');
}
closurefun();
//输出 hello
```

### 在函数内部返回匿名函数，并调用

```
function closureFun(){
	$func = function($str){
		echo $str;
	};
	return $func;
}
$example = closureFun();
$example('hello');
//输出 hello
```

### 将匿名函数作为参数传递

```
function example($func){
	$func('hello');
}
$closureFun = function($str){
	echo $str;
};
example($closureFun);
//也可以直接传递
example(function($str){
	echo $str;
	});
```
