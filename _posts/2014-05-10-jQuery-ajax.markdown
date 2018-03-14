---
layout:     post
title:      "jQuery ajax"
subtitle:   "jQuery ajax"
date:       2014-05-10 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

## jQuery中发送ajax请求

```
$(function(){
	$.ajax({
		url:'receive.php', //数据发送地址
		type: 'post', //数据传输方式
		data:{menu:1}, //需要传送的数据
		dataType:'json', //返回的数据格式
		success:function(data){ //成功接收到数据执行的函数
			//遍历数组
			$.each(data,function(k,v){
				//重组数据分配到页面
				var str = '<p>'+v.text+'</p>';
				$('#box').append(str);
			})
		}
	})
})