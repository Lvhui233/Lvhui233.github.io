---
layout:     post
title:      "CSS3 基础与响应式"
subtitle:   "CSS3 basic and responsive"
date:       2014-05-15 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - CSS3
---

## 选择器

CSS3的选择器的一部本用法和jquery抓取元素类似,这里只介绍一下特殊的

### 文本选择器

```
//为文本的第一行设置样式
p:first-line{
	color = "red";
}

//为文本首字母设定样式
p:first-letter{
	font-size:20px;
}

//在选中元素内容前插入内容
p:before{
	content:"hello";
}

//在选中元素内容后插入内容
p:after{}
```

## 基础样式

### RGBA颜色设置

```
//前三个参数分别代表红绿蓝,取值0-255，最后一个参数是透明度,0.5即为半透明
p{
	background:rgba(255,0,0,0.5);
}
```

### 字体单位

- px 以像素为单位

- em 以父元素为参考单位

- rem 以根元素`<html>`为参考单位

### 文本溢出设置

`text-overflow`属性规定文本溢出的规则

属性值
- clip 修剪文本
- ellipsis 显示省略号来代表被修剪的文本
- string 使用指定字符代表被修剪的文本

```
//强制不换行
p{
	width:200px;
	height:300px;
	white-space:nowrap;
	text-overflow:ellipsis;
	ovweflow:hidden;
}
```

### 文字阴影

```
//四个参数为(水平阴影位置,垂直阴影位置,阴影距离,颜色)
text-shadow:5px 5px 10px #333;
```

### 盒子阴影

```
//参数(水平阴影位置,垂直阴影位置,模糊距离,阴影尺寸,颜色)
box-shadow:-10px 10px 20px 2px red;
```

### 元素的最大最小值

```
max-width
min-width
max-height
min-height
```

### box-sizing怪异模式

- content-box border和padding不计算入width

- border-box border和paddin算在width之内,就是怪异模式

### 分栏

```
//设置每一栏宽度
column-width:300px;
//设置列间距
column-gap:20px;
//设置列间分割线
column-rule:2px solid blue;
```

### 背景图尺寸

```
background-size: 100% 100%;
//保证宽度100% 
background-size:contain;
//保证高度100% 
background-size:cover; 
```

### 线性渐变颜色

```
//第一个参数是起始位置,其他参数是颜色,可以有多个渐变色
-moz-linear-gradient(left top,green,transparent);
```

### outline轮廓线

outline是绘制于元素周围的一条线,位于边框边缘的外围,可起到突出元素的作用,轮廓线不同于边框，不占用空间尺寸,只有在获得焦点或者激活时呈现。

```
p:hover{
	outline:solid 3px red;
}
input:focus{
	outline :solid 2px blue;
}
```

## 响应式设计

根据不同的条件使页面使用不同的样式

### 嵌入样式写法

```
<style type="text/css">
	@media only screen and (max-width:600px){
		body{
			background:red;
		}
	}
	@media only screen and (max-width:600px)and(min-width:400px){
		body{
			background:green;
		}
	}
</style>
```

### 引入样式写法

```
<link rel="stylesheet" type="text/css" href="A.css" media="screen">
<link rel="stylesheet" type="text/css" href="B.css" media="screen and(max-width:800px)">
<link rel="stylesheet" type="text/css" href="C.css" media="screen and(max-width:600px">
```
