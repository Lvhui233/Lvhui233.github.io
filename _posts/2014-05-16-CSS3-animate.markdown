---
layout:     post
title:      "CSS3 动画效果"
subtitle:   "CSS3 animate"
date:       2014-05-16 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - CSS3
---

## 动画效果

### 过渡

transition可以有四个参数,分别是过渡的属性,过渡时间,开始过渡前的延迟时间,过渡的变化速率

变化速率参数
- ease 贝塞尔曲线
- linear 匀速
- ease-in 加速
- ease-out 减速 
- ease-in-out 先加速后减速

```
transition:width 2s,height 3s 2s linear
```

### 变形

transform设定元素旋转

- 旋转`transform:rotate(30deg);`
- 平移`transform:translate(100px,50px);`
- 缩放`transform:scale(1.5,0.6);`
- 扭曲`transform:skew(30deg,60deg);`

```
transform: rotate(30deg); 
//deg表示度数，默认顺时针旋转 
//设置旋转基点,基地的位置是指在元素内部的位置 
transform-origin:20px 30px; 
```
### animation动画

animation的参数

1. 定义动画名称
2. 动画播放时长,默认0
3. 变化速率
4. 延迟时间
5. 循环次数,默认1,infinite为无限次数
6. 是否应该轮流反向播放动画

animation-play-state 动画播放状态(running,paused)

keyframes关键帧设定运动节点

```
p{
	width:100px；
	height:100px;
	animation:move 2s 3s infinite;
}
@keyframes{
	from{
		width:100px；
	}to{
		width:900px;
	}
}
//如有多段变化
@keyframes{
	0%{
		width:100px；
	}50%{
		width:900px
	}100%{
		width:100px；
	}
}
```

## swiper的使用

swiper可以简化代码的使用,常用于移动端网站的内容触摸滑动,也可以用于微场景等

详细使用见:[swiper中文网](http://www.swiper.com.cn/)
