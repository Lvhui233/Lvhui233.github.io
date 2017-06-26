---
layout:     post
title:      "HTML 列表与表单"
subtitle:   "HTML list and form"
date:       2017-04-20 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - HTML
---


## 路径

### 相对路径

从起点开始查找文件，起点的路径是当前文件所在目录。
上行用../

### 绝对路径

http：//网址

## 列表

- 有序列表ol：order list
- 无需列表ul：unorder list 
- 自定义列表dl，dt定义列表标题，dd定义列表项

## 表单

	`<form action="数据接收地址" method="发送方式post/get"></form>`

### input标签

type属性

```
单行文本：text 
密码password 
单选框：radio 
复选框：checkbox 
隐藏域：hidden 
提交按钮：submit 
文件域：file 
重置按钮:reset 
按钮: button 
```

input标签共有属性

```
type控件类型
value默认值
name用于服务器获取数据
```

单选和多选：value为被选中所提交的值、checked为默认选中项、name用于服务器获取数据

### 文本区域

```
<textarea></textarea>
```

### 下拉框

```
	<select>
		<option> </option>
	</select>
```

#### 下拉框属性

- name用于指定列表框的名字
- size为显示的项目数，缺省值为1
- multiple设置后可以多选</h3>

## iframe标签

`iframe标签`可以在当前页面插入其他页面或视频

```
//视频
<iframe height=498 width=510 src='http://player.youku.com/embed/XMTkwOTY0MjM4NA==' frameborder=0 'allowfullscreen'></iframe>
//页面
<iframe src="http://taobao.com" width="800" height="400"></iframe>
```