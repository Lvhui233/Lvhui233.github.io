---
layout:     post
title:      "javascript 函数与数组"
subtitle:   "javascript function and array"
date:       2014-04-30 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

## javascript 函数

```
function函数名(){
	函数体
	return //返回值
}
```

### 变量作用域

1. 局部变量,在函数内部定义的变量,只能在函数内部访问到
2. 全局变量,非局部变量,在全局都可以访问到

## 内置顶层函数

- 内置: ECMAscript自带的函数
- 顶层: 在页面的任何地方皆可调用

### Number()转换成数值类型

- 布尔值转换成0或1
- 数字转化成本身,将无意义的后导0去掉
- undefined 转换为NaN
- 空字符串转为0,其他转换不了的值返回NaN

### parseInt()将字符串转为整数

自动忽略字符串前面的空格，直到找到第一个非空的 数值字符串，如果字符串的第一个字符不是空格、数字、-， 
那么返回NaN

### parseFloat()将字符串转为浮点数

字符串当中的.只有第一个有效，其他的都是无效的,
如果是整数,只会返回整数

### isNaN() 检测参数是否为非数字值

如果能转换成数值返回假,不能转换成数值类型,返回真。

### eval()字符串解析

用javascript语法来解析字符串内容

## 数组

### 声明数组

```
\\先声明后赋值
var a=[];a[0]=1;a[1]=2

\\直接赋值 
var a = [1,2];

\\通过构造函数声明
var a = new Array(1,2,3)
```

### 遍历数组

用for循环遍历数组

### 访问数组

```
//通过下标访问
var a = [1,2,3];
alert(a[0]);

//获取数组长度
var long = a.length
```

### 元素的追加与删除

```
var fruit = ['apple','banana','orange','pear'];

//向数组末尾追加
fruit.push('pineapple');

//向数组开头追加
fruit.unshift('pineapple');

//删除数组最后一个元素,返回删除的元素
fruit.pop();

//删除数组的第一个元素,返回删除的元素
fruit.shift()
```
#### 万能添加与删除函数splice

```
fruit.splice(起始位置,删除数量,添加的元素);

```

### 截取数组

```
//截取时包含起始位置但不包含结束位置的元素
var re = fruit.slice(起始位置,结束位置);

//从第2位截取到最后
var re = fruit.slice(2);

//从第1位截取到倒数第2位
var re = fruit.slice(1,-2);
```
### 数组转换成字符串

```
var string = fruit.join('');
```

### 数组连接

```
var newArray = fruit.concat(fruit);
```

### 数组排序

```
var shuzu = [10,56,23,6,403,87,3,5,55];
	
//用来排序的函数
	function sortNum(x,y){
		return y-x;
	}
	var re = shuzu.sort(sortNum);
	document.write(re);
```