---
layout:     post
title:      "jQuery 基本操作"
subtitle:   "jQuery basic operate"
date:       2014-05-09 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

## 链式操作

jquery可以用链式调用,节约很多代码

## 元素的显示与隐藏

```
//改变css的diplay属性
$('#box').css('display':'none');

//隐藏与显示方法
$('#box').hide();
$('#box').show();

//自动判读显示与隐藏切换
$('#box').toggle();

//淡入淡出
$('#box').fadeIn(2000);
$('#box').fadeIn(1000,'linear');
```

## animate动画

```
//四个参数分别是结束时的属性,运动事件,运动方式,回调函数
$('#box').animate({'width':'300px','height':'400px'},3000,'linear',function(){
		alert('finish');
	})

//清除元素当前运动(可以解决运动叠加问题)
$('#box').stop();
```

## 鼠标点击过快与移入移出过快问题

通过设置控制变量,以及setTimeout定时器延时触发来解决

## jQuery对属性的操作

attr方法

```
//获得元素属性
var re = $('#box').attr('name');

//改变与添加元素属性
$('#box').attr('class','fruit');

//删除元素属性
$('#box').removeAttr('name');
```

prop方法多用于复选框
```
//获得元素属性(返回值true或false)
var re = $('#box :checkbox').prop('checked');

//改变与添加元素属性
$('#box :checkbox').prop('checked',true);

//删除元素属性
$('#box :checkbox').removeProp('checked');
```

### 获得与设置表单value值

```
var pwd = $('#box input[type=password]').val();
$('#box input[type=text]').val('name');
```

## class属性的操作

```
//添加class属性
$('#box').addClass('fruit');

//删除class属性
$('#box').removeClass('fruit');
```

## 获得与设置css样式

```
//获得css样式
$('#box').css('height');

//设置css样式
$('#box').css('width','200px');
```

## 元素的位置

```
//获得元素距离页面顶部的实际位置
$('#box').offSet().top

//获得定位元素的left值
$('#box').position().left
```

## 元素尺寸的操作

```
//获得内容宽度
$('#box').width();

//获得内容和内边距宽度
$('#box').innerWidth();

//获得总宽度(内容+内边距+边框)
$('#box').outerWidth();
```

## 节点操作

```
//追加新元素
$('#box').append('<p>新来的</p>'');
$('#box').prepend('<p>新来的</p>'');

//将#title插到2好p标签之后
$('#box p').eq(2).after($('#title'));

//包裹
$('#box p').wrap('<u class="hahha"></u>')
$('#box p').wrapAll('<u class="hahha"></u>')

//替换
$('#box p').eq(3).replaceWith('<h1>hello</h1>');

//清空元素
$('#box').empty();

//删除元素
$('#box').remove();

//复制元素(true会复制全部子节点，默认false)
var obj = $('#box').clone();
```

## 事件

### 绑定事件

普通绑定

```
$('#box p').click(function(){
		//$this表示当前时间源,index()方法获得序号
		var index = $this.index();
		alert(index);
	})
```

给未来元素绑定事件

- 用on给元素绑定事件

```
//on可以绑定一个或多个事件
$('#box').on('click mouseenter',function(){
		alert('great');
	})

//给子元素绑定事件
$('#box').on('click','p',function(){
		alert('success');
	})

//解除绑定事件
$('#box').off('click');
```

- 直接在html中绑定

```
function func(){
	alert('success');
}
$('#box').click(function(){
		$('#box').append('<p onclick="func()">new tag</p>');
	})
```

### 移入移出事件

- jQuery中移入与移出事件分别是mouseenter和mouseleave

- jQuery会自动解决鼠标和事件源之间有其他元素的问题

```
//hover方法同时设置移入移出执行的方法
$("#box").hover(function(){//移入时执行
		$(this).css({'background':'red'});
	},function(){//移出时执行
		$(this).css({'background':'blue'});
	})
```

### 仅执行一次的事件

```
//用法和on类似不过只触发一次
$('#box').one('click mouseenter',function(){
		alert('success');
	})
```

### 触发特定事件

```
//触发表单提交事件
$('form').trigger('submit');
```

### 事件对象

```
//鼠标相对于文档左侧距离
$('#box').click(function(e){
	var left = e.pageX;
})
```

## 无缝轮播图

1. 在轮播条最后添加第一张图片，当轮播到最后张图片时（也就是放在最后的第一张图片时），当再次运动时，判断控制变量的值，然后瞬间改变定位值，让器位置换到第一张图片，接着改变控制变量的值，让其滑动到第二张图片，就可以达到无缝连接的视觉效果

2. 让第一个宽度渐渐变小，然后回调函数将第一个元素追加到最后，让最后一个元素宽度再变回来。

## jQuery对象与原生对象的互相转换

```
//jquery抓取得对象转换成原生
$('#box')[0]

//原生对象转换成jquery对象
$(document.getElementById('#box'))
```