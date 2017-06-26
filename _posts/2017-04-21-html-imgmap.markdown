---
layout:     post
title:      "HTML 图像地图"
subtitle:   "HTML imgmap"
date:       2017-04-21 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - HTML
---


## 注释

```
<--要注释的文字-->
```

## 文字标签

```
<strong>加粗</strong>
<em>斜体</em>
<u>下划线</u>
```

## 图像地图

点击图片的不同位置，打开不同的页面,需要给图片加usemap属性

```
<img src="dog.jpg" alt="" usemap="#Map"/>
<map name="Map">
    <area shape="circle" coords="184,198,26" href="http://baidu.com" target="_blank">
    <area shape="circle" coords="313,202,25" href="http://sohu.com" target="_blank">
    <area shape="rect" coords="-2,149,99,236" href="http://so.com" target="_blank">
    <area shape="poly" coords="395,105,403,80,404,60,401,40,399,25,389,14,377,9,369,7,346,15,336,24,325,30,320,39" href="http://sina.com.cn" target="_blank">
</map>
```    

用dreamwea进行设置更快捷

