---
layout:     post
title:      "CSS 定位和背景"
subtitle:   "CSS position and background"
date:       2017-04-24 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - CSS
---


## 定位属性

### 相对定位

1. 全脱离文档流 
2. 文档流里的位置还被保留着
3. 对于原来的位置进行定位

### 绝对定位

1. 完全脱离文档流
2. 不保留原来的位置
3. 参照于离他最近的 有定位属性的 父级元素进行定位

### 固定定位

1. 完全脱离文档流
2. 原来的位置不被保留
3. 参照于浏览器可视区域进行定位

### 层级z-index

只有有定位属性的元素才有层级的概念,定位元素的前后顺序是按照层级(z-index)来定的,
层级默认值是0,如果层级一样，后来者居上

## 背景

```
//背景颜色
background-color
//背景图片
background-image
//背景平铺
background-repeat 
//背景图片位置
background-position
//综合写法的参数顺序:背景颜色 背景图 平铺方式 x轴位置 Y轴位置
//如果不需要哪个参数,就直接不用写 
background: green url(xiaogou.jpg) no-repeat 200px 88px;
//给背景切圆角
border-radius:50%;
```

## css sprites背景精灵

在一个有限大小的区域内，显示大背景图的某一部分内容

## cursor属性

设置鼠标悬浮在标签上时的样式

## 透明度

- 火狐等w3c浏览器:`opacity:0.6 ` 
- IE低版本:`filter: alpha(opacity=60)`

## 直接给颜色加透明

```
rgba(255,255,255,0.6)
//最后一个值控制透明度
```

## visibility属性

visibility隐藏元素后,元素的位置还被保留

```	
visibility: hidden;
```

## li列表样式

```
//列表样式
list-style:none;
```

## hover的妙用

元素上设置hover，可以在鼠标移入父元素时子元素发生变化
也可以用来设置二级菜单

```
#out:hover .in{
	background: yellow;
}
```



