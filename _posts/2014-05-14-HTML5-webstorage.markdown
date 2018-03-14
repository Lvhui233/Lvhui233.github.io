---
layout:     post
title:      "HTML5 web storage"
subtitle:   "HTML5 web storage"
date:       2014-05-14 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - HTML5
---

## Web storage特点

Web Storage与session和cookie类似，Web Storage也有分两类sessionStorage和localStorage，这两个差别就跟session和cookie一样，sessionStorage关闭浏览器后过期，localStrage不会过期，但是跟cookie不一样的是没有过期时间。

- 容量大，5M~10M
- 不会随着回话来传输
- 接口丰富,读取和写入方便

## 浏览器检测(需要搭建服务器环境访问)

```
<script type="text/javascript">
	var h1 = document.getElementById('h1');
	var h2 = document.getElementById('h2');
	if(window.sessionStorage){
		h1.innerHTML = "支持sessionStorage"；
	}else{
		h1.innerHTML = "不支持sessionStorage";
	}
	if(window.localStorage){
		h2.innerHTML = "支持localStorage";
	}else{
		h2.innerHTML = "不支持localStorage";
	}
</script>
```

## sessionStorage

1. 只要浏览器串口不关闭就会一直保存
2. 只允许在一个标签中操作,也不支持ctrl+click操作
3. 适合在短时间使用的业务中

```
//存储指定字段
sessionStorage.setItem(key,value)
//获得指定字段的值
sessionStorage.getItem(key)
//删除指定字段的本地存储值
sessionStorage.removeItem(key)
//sessionStorage的项目数
sessionStorage.length 
//清除所有sessionStorage数据
sessionStorage.clear()
```

## localStorage

1. 存储没有时间限制
2. 多个标签可共享

存储查询等操作与sessionStorage类似


