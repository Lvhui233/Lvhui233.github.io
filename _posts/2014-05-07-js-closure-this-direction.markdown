---
layout:     post
title:      "javascript 闭包与this的指向"
subtitle:   "javascript closure and this direction"
date:       2014-05-07 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

## 闭包

### 从外部读取局部变量

子函数可以读取父函数内部声明的局部变量

```
function f1(){
	var n = 123;
	function f2(){
		alert(n);
	}
	return f2;
}
var result = f1();
result(); //123
```

其中f2函数就是闭包,f2被赋予了全局变量result,而f2又依赖于f1，所以f1在运行之后没有自动销毁,始终存在于内存中

具体可以看[阮一峰老师的博客](http://http://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html)

### 函数的自调用

函数的底调用也属于闭包

```
(function(a){
	alert(a*a);
	})(3)
```

## this的指向问题

在事件函数中this指向事件源

```
box.onclick = function(){
	this.style.color = 'red';
}
//this指向box
```

在对象内部指向当前对象

```
var object = {
	name : "mary",
	getNameFunc : function(){
		alert(this.name);
	}
}
//this指向object对象
```

## js中的数据传址与传值

- 传值：基本类型数据赋值时,直接将数据值传递过去

- 传址：引用类型(对象)数据赋值时,只传递数据存储地址,不赋值值
 