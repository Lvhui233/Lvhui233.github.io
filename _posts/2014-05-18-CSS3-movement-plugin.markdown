---
layout:     post
title:      "CSS3 3D与运动插件"
subtitle:   "CSS3 3D and movement plugin"
date:       2014-05-18 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - CSS3
---

## 3D转换

通过css3 3D转换,能够在2D空间内模拟3D运动

```
//定义d3环境
transform-style: preserve-3d;
//定义景深
perspective: 1000px;
```

## jquery的easing运动插件

先在头部引入jquery的easing js文件

```
$("#box").animate({"left:500px"},2000,"easeOutBounce");
```

easing[缓动函数速查表](http://easings.net/zh-cn)

## animate.css运动库

在头部引入相应css文件,给元素添加特定class就能执行运动

运动效果预览[daneden.github.io/animate.css ](http://daneden.github.io/animate.css )

下载地址[github.com/daneden/animate.css](http:github.com/daneden/animate.css)