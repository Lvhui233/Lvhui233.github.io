---
layout:     post
title:      "javascript 节点与元素位置"
subtitle:   "javascript node and element position"
date:       2014-05-05 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

## 节点

### 节点的属性

通过节点的属性,能够获取节点之间的管，并通过关系,准确快速的的获取到相应节点的对象。

```
var box = document.getElementById('box');

//获得父节点的引用
box.parentNode

//获得子节点集合
box.childNodes

//获得第一个子节点的引用
box.firstChild

//获得最后一个子节点的引用
box.lastChild

//获得下一个兄弟节点的引用
box.nextSibling

//获得上一个兄弟节点的引用
box.previousSibling
```

### 节点的方法

#### 创建元素节点

1. 创建空元素节点
```
var new_node = document.creatElement("元素标签名");
```
2. 创建属性节点
```
new_node.setAttribute(属性名,属性值);
```
3. 创建文本节点
```
new_node.innerHTML = "";
```

#### 追加到页面当中

```
//在指定元素节点的最后一个子节点后添加节点
父对象.appendChild(追加的对象);

//插入到某个字节点之前
父对象.insertBefore(要插入的对象,原有的对象);
```

#### 删除节点

```
父对象.removeChild(删除的对象);

//如果要删除对象最好也清空内存
对象=null；
```

#### 替换节点

```
父对象.replaceChild(新节点,被替换的节点);
```

#### 复制节点

```
待复制节点.cloneNode()
//该方法有一个参数(true或false),true会复制所有子节点,false只复制本节点
```

##元素的位置与尺寸

### 获得元素的位置

offsetTop offsetLeft
返回元素相对于父元素的坐标(left top 值)
1. 设定了position属性
2. 没有设定position属性,如果前辈元素也没有定位属性,那么是相对于浏览器窗口的距离

### 元素尺寸的属性

- 获得元素实际的高度和宽度
offsetWidth offsetHeight(数值类型)

- 获得可见区域的高度和宽度
document.documentElement.clientWidth
document.documentElement.clientHeight

### 获得元素滚动条位置

- 滚动条位置
scrollTop scrollLeft
- 滚动元素宽高
scrollWidth scrollHeight





