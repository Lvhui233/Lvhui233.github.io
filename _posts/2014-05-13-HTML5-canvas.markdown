---
layout:     post
title:      "HTML5 画布"
subtitle:   "HTML5 canvas"
date:       2014-05-13 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - HTML5
---

## canvas

canvas用来定义一块画布,在js中进行绘制
canvas不能用css设置宽高

### 定义画布

```
<canvas width='500px' height='500px' id='canvas'></canvas>
//js获得画布对象
var c = document.getElementById('canvas').getContext();
```

### 绘制矩形

```
//实心矩形
//设置颜色
c.fillStyle = 'yellow';
c.fillRect(50,50,100,200);

//空心矩形
c.strokeStyle = 'red';
//设置画线宽度
c.linWidth = 10;
c.strokeRect(10,20,70,100);

//擦除固定矩形区域
c.clearRect(40,100,50,30);
```

### 绘制线条

```
//开启路径
c.beginPath();
//移动到起点
c.moveTo(30,40);
//连线
c.lineTo(100,200);
//设置线条
c.lineStyle = 'blue';
c.linewidth = 6;
//拐角样式(bevel,round,miter)
c.lineJoin = 'round'
//绘制线条
c.stroke();
```

### 绘制多边形

```
c.beginPath();
cv.moveTo(200,400);
cv.lineTo(500,400);
cv.lineTo(350,50);
//结束路径
cv.closePath();
c.fillStyle = 'red';
//填充时会自动闭合路径
c.fill();
```

### 画布控制

```
//缩放画布
c.scale(1.5,0.7);
//图像水平位移
c.traslate(50,50);
//画布旋转(单位是弧度)
c.rotate(30*(Math.PI/180));
```

### 绘制弧线

```
cv.arc(400,300,150,0,90*(Math.PI/180));
cv.strokeStyle = 'yellow';
cv.lineWidth = 6;
cv.stroke();
```

###  绘制文字

```
//设置文字属性
cv.font = '40px 微软雅黑';

cv.fillStyle = 'yellow';
//在画布中写入文字
cv.fillText('hello',100,100);


//设置文字水平位置
//cv.textAlign = 'center';
//设置垂直对齐
cv.textBaseline = 'middle';
cv.strokeStyle = 'greenyellow';
cv.strokeText('hello',300,200);

//画参考线
cv.beginPath();
cv.moveTo(0,200);
cv.lineTo(800,200);
cv.strokeStyle = 'white';
cv.stroke();

cv.beginPath();
cv.moveTo(300,0);
cv.lineTo(300,500);
cv.stroke();
```

### 画布中写入图像

```
c.drawImage(img,画布x坐标,画布y坐标);
```

### 图像平铺

```
c.rect(0,0,500,500);
c.fillStyle()=c.createPattern(img,重复方式);
```

### 获得指定区域的图片数据

```
var d = c.getImageData(160,350,200,200);
c.putImageData(d,500,300);
```
