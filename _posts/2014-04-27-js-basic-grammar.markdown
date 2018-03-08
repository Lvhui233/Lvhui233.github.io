---
layout:     post
title:      "javascript基本语法"
subtitle:   "javascript basic grammar"
date:       2014-04-27 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---


## javascript放置引用

### 嵌入式调用

`<script type= "text/javascript"></script>`

### 在超链接或重定向位置调用js代码

- 超链接格式`javascript:alert("超链接")`
- 重定向格式`action="javascript:alert('表单')"`

### 在事件后进行调用

### 调用外部js文件

`<script src="main.js"></script>`

## 输出工具

- `alert();`弹窗,会以文本原格式输出
- `document.write()` 输出到页面,会以html语法解析里面的内容
- `prompt("提示文字","默认值")` 输入框,有返回值

## 注释

- 行内注释 `//注释内容`
- 块注释 `/*注释内容*/`

## 变量

存储数据的容器

```
//声明变量
var abc;
abc='hello';
//声明多个变量
var a=1;b="2",c=3;
```

### 变量的命名规范

必须以字母或_或$开头,余下部分可以是任意字母、数字或者_及$

###变量类型

1. Undefined(声明但没有赋值的变量类型)
2. Null(空对象)
3. Number
4. String
5. Boolean
6. Object(包含相关属性和方法的集合)

### 检测变量类型

函数`typeof()`会返回一个字符串

