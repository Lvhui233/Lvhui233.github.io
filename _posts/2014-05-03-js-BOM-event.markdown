---
layout:     post
title:      "javascript BOM与事件"
subtitle:   "javascript BOM and event"
date:       2014-05-03 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

## BOM

Browser Object Model 浏览器对象模型
window对象是BOM中所有对象的核心

### window对象

```
//定时器函数(时间以毫秒为单位)
setInterval(函数,时间);
//仅执行一次的定期器
setTimeout(函数,时间);
//清理定时器
clearInterval(定时器名);
clearTimeout(定时器名);
//弹窗提示
alert();
//确认提示
confirm(提示语句);
//弹出输入框
prompt(提示语,默认值);
```

### history对象

history对象包含用户访问过的URL,它是window对象的子对象

```
//属性
//length属性返回浏览历史列表中的URl数量
history.length

//方法
//加载history列表中的前一个url
history.back();

//加载history列表中的下一个url
history.forward();

//指定加载历史列表中的某个url
history.go(number);
```

### location对象

```
//属性
//href属性加载页面
location.href = 'http://google.com';

//方法
//assign()加载新页面
location.assign('http://google.com');

//replace()替换url,不生成历史记录
location.replace('http://google.com');

//重新加载页面(刷新)
location.reload();
```

## js中的事件

### 绑定事件

1. 在脚本中绑定
2. 直接在HTML元素绑定 `<div onclick="foo('hello')"></div>`

### 鼠标事件

- onclick 鼠标单击事件
- ondblclick 鼠标双击事件
- onmousedown 鼠标按下时的事件
- onmouseup 鼠标抬起时的事件
- onmousemove 鼠标移动事件,在内部移动也会触发
- onmouseover 鼠标移入事件
- onmouseout 鼠标移出事件

### 键盘事件

- onkeyup 抬起键事件
- onkeydown 按下键事件
- onkeypress 按下并放开任何字母数字键时触发

### 表单事件

- onsubmit 提交时触发的事件
- onblur 失去焦点时触发的事件
- onfocus 获得焦点时触发的事件
- onchange  内容发生变化并失去焦点时触发的事件

### 其他事件

- onload 页面事件
- onresize 窗体事件
- onscroll 滚动条事件

### 事件监听

```
var box = document.getElementById('box');
var fn = function(){
	alert('hi');
}
//IE
box.attachEvent('onclick',fn)

//firefox
box.addEventListener('click',fn)

//移出事件监听
box.detachEvent('onclick',fn);
box.removeEventListener('click',fn);
```