---
layout:     post
title:      "javascript 事件对象与日期对象"
subtitle:   "javascript event object and date object "
date:       2014-05-06 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

## 事件对象

用来记录事件发生时的相关信息的对象
1. 只有放事件发生的时候才产生,只能在处理函数内部访问
2. 处理函数运行结束时自动销毁

### 获取事件对象

```
var box = document.getElementById('box');

//IE
box.onclick = function(){
	var ev = window.event
}

//firefox
box.onclick = function(e){
	var ev = e;
}
```

### 事件对象的属性

1. 鼠标事件

```
//事件发生时,鼠标相对于浏览器的位置
clientX
clientY

//事件发生时,鼠标相对于事件源的位置
//IE
offsetX
offsetY

//firefox
layerX
layerY
```

2. 键盘事件

```
// 获得键盘码(需要用fromCharCode转换)
keyCode

//判断alt键是否被按下,按下时true反之false,布尔值,用在keydown事件里
altKey
ctrlKey
shiftKey
```

## 事件流

### 事件流分类

1. 冒泡型事件
有明确的事件源到不确定的事件源依次向上触发

2. 捕获型事件(IE不支持)
不确定的事件源到确定的事件源依次向下触发

### 阻止事件流(事件对象)

```
//IE
事件对象.cancelBubble = true;

//firefox
事件对象.stopPropagation();
```

### 阻止浏览器默认行为

```
//IE
事件对象.returnValue = false;

//firefox
事件对象.preventDefault();

//html中阻止
<a href="javascript:void(0);"></a>
```

## 日期对象

js中日期也是内置对象,对日期进行获取和操作,必须实例化对象

### 创建日期对象

可传入的参数格式
1. "时:分:秒 月/日/年"  "月/日/年 时:分:秒" 字符串
2. 年,月,日,时,分,秒 不能加" "

```
//不传参获取当前时间
var dateobj = new Date();
```

### 获取日期信息的方法

```
getFullYear()
//获得月份(0-11)
getMonth()
getDate()
getHours()
getMinutes()
getSeconds()
//获得日期是周几(0是周日);
getDay()
//获得时间戳
getTime()
```

### 设置日期的方法

```
setFullyear()
setMonth()
setDate()
setHours()
setMInutes()
setSeconds()
setTime()
```