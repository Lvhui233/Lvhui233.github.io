---
layout:     post
title:      "jQuery 选择器与筛选"
subtitle:   "jQuery selector and filter"
date:       2014-05-08 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

## 选择器

除伪类选择器外,所有的css选择器都可以在jQuery中使用

```
//选择#a中所有的子类p标签
$("#a>p")

//选则紧邻在#a后的那个p标签
$("#a+p")

//选择#a后面所有同级p标签
$("#a~p")

//选择#a里的第一个p标签
$("#a p:first")

//选择#a里id不是b的所有p标签
$("#a p:not(#b)")

//选择#a里序号是偶数的p标签
$("#a p:even")
//选择#a里序号是奇数的p标签
$("#a p:odd")

//选择#a里的2号p标签
$("#a p:eq(2)")

//选择#a里序号大于2的p标签
$("#a p:gt(2)")

//选择#a里内容包含abc的p标签
$("#a p:contains(abc)")

//选择#a里空的p标签
$("#a p:empty")

//寻找#a里包含span标签的p标签
$("#a p:has(span)")

//选择#a里有class属性的p标签
$("#a p[class]")
//选择#a里name属性为fruit的p标签
$("#a p[name=fruit]")
//选择#a里有class属性且name属性为fruit的p标签
$("#a p[class][name=fruit]")

//选择的是#a里的p标签的父级元素的第2个子元素,这个子元素是p标签才行
$("#a p:nth-child(2)")

//选择的是#a里p标签的父级元素中的第2个p标签
$("#a p:nth-of-type(2)")
```

## 筛选

```
//与选择器用法类似
$('#a p').eq(1) 
$('#a p').first() 
$('#a p').has('span') 
$('#a p').not('#one') 

//选择#a里的3-7号p标签(包含3不包含7)
$('#a p').slice(3,7)

//选择#a里p标签里的span标签
$('#a p').find('span')

//选择#a后面的兄弟元素
$('#a p').next()

//选择的是#a的父元素
$('#a').parent()

//选择#a所有父元素中class是fruit的
$('#a').parents('.fruit')

//选择#a的所有p标签亲兄弟元素
$('#a').siblings('p')
```

