---
layout:     post
title:      "CSS 盒模型与浮动"
subtitle:   "CSS box and float"
date:       2014-04-23 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - CSS
---


## 盒模型

一个块元素所占的宽高由内容、内边距：padding、边框：border、外边距：margin决定

### 外边距

左右边距会累加，上下边距会合并
当父元素没有内外边距时其子元素的内外边距会加到父元素上，只需给父元素加内边距即可解决问题

## 块元素居中

可以设置左右边距为`auto `
`margin：0 auto ;`

## 全局reset

通常要在css的最前面进行,浏览器会给某些元素设置默认的内外边距，为了不影响我们对元素精准的控制，
一般在写代码之前要先清理掉默认的内外边距

```
*{
	margin：0;
	padding：0;
}
```

## 隐藏

```
overflow //用来设置溢出 
overflow:hidden //溢出隐藏 
display: none; //隐藏元素
```

## 浮动属性

float元素特点：
1. 让块级元素排列到同一行 
2. 如果浮动元素的上一行没有浮动属性，那么浮动元素是跑不上去的
3. 浮动元素是脱离文档流的
4. 一个正常元素，在排列自己位置的时候，会无视掉前面的浮动元素，但文字会环绕浮动元素，不会被遮挡 

## 经典布局

1. 弹性布局
2. 双飞翼布局（圣杯布局）

## 子元素浮动无法撑起父元素时的处理方法

给父元素加`overflow：hidden`可以解决,或者再在父元素里加一个div,
给此div加`clear：both`,也可以解决。
