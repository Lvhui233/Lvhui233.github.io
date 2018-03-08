---
layout:     post
title:      "javascript 数学对象与字符串对象"
subtitle:   "javascript math object and string object"
date:       2014-05-02 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

## 数学对象

```
//取绝对值
var num = Math.abs(-6);

//取整(四舍五入)
var num = Math.round(12.678);

//向上取整
var num = Math.ceil(2.33);

//向下取整
var num = Math.floor(3.98);

//取随机数(0到1之间但是取不了0和1)
var num = Math.random();

//取x,y之间随机整数(可以取到最大最小值)
var num = Math.floor(Math.randow()*(y+1-x)+x);
```

## 字符串对象

### 查询字符串内容

```
var str = abcdefg

//获取字符串长度
var len = str.length;

//获取个别位置上的字符
var letter = str[2];
var letter = str.charAt(2);

//获得个别位置上字符的Unicode编码
var uni = str.charCodeAt

//将Unicode编码转换成原始字符
var letter = fromCharCode(100);

//获得字符在字符串中第一次出现的位置
var position = str.indexOf('c');
//最后一次出现的位置
var position = str.lastIndexOf('c');

//查询字符串中有没有指定字符(若有返回值即是指定字符)
var re = str.match('bc');
```

### 替换字符

```
var str = 'dsfdsadfdsafdgdfhgfd'

//replace默认只替换第一个匹配到的字符
 var newStr = str.replace('fd','ab');

//replace与match配合替换全部匹配字符
var newStr = str
while(newStr.match('fd')){
	newStr = newStr.replace('fd','ab');
} 
```

### 截取字符串

- `var newStr = str.slice(起始位置,终止位置);`
如果不设置结束位置则一直截取到最后

- `var newStr = str.substr(起始位置,截取位数)：`
如果不设置结束位置则一直截取到最后

### 字符串切割成数组

```
var str = "apple-banana-pineapple";

var arr = str.split('-');
```

### 大小写转换

```
var str = 'HelloWorld';

//转成大写
var upper = str.toUpperCase();

//转成小写
var lower = str.toLowerCase();
```