---
layout:     post
title:      "javascript DOM操作"
subtitle:   "javascript DOM operating"
date:       2014-05-04 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

## DOM 

document object model
可以对html元素的样式,内容,属性进行动态的操作

### document对象

```
//属性
// 返回或设置文档标题
document.title

//方法
//返回指定id的对象的引用
document.getElementById(idname);

//返回带有指定标签名的对象的集合
document.getElementsByTagName(tagname);

//返回带有指定name指定名称的对象的集合
document.getElementsByName(name);

//返回带有指定class指定名称的对象的集合
getElementsByClassName(classname);
```

### 对元素内容的操作

- innerHTML 设置与获取标签内的内容,识别html标签
- innerText 设置与获取标签内的文字(IE)
- textContent 设置与获取标签内的文字(firefox)

### 对元素属性的操作

1. 特定属性: id,class,href,src
2. 任意属性

```
//获取属性
getAttribute(属性名);

//设置属性
setAttribue(属性名,属性值);
```

### 对元素样式的操作

```
//设置与获取行内样式
对象.style.css样式

//获取实际样式不能设置
//IE
对象.currentStyle.CSS样式

//firefox
getComputedStyle(对象,null).css样式
```

## 数据的几种调试输出方法

```
//弹窗
alert();

//输出到标题栏
document.title = 'hello';

//输出到控制台
console.log('输出内容');
```