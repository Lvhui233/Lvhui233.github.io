---
layout:     post
title:      "javascript运算符"
subtitle:   "javascript operator"
date:       2014-04-28 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

## 算数运算符

加`+`减`-`乘`*`除`\`取余`%`自增`++`自减`--`

## 比较运算符

- 字符串之间比较时,会先转换成ASCII码然后进行比较他们的第一个字母
- 字符串和数值比较时,会先尝试将字符串转化成数值类型进行比较,若不能转换,
返回假
- 数值和布尔值比较,会将布尔值转化为数值,true为1,false为0

## 赋值运算符

`= += -= *= /= %=`

## 逻辑运算符

- 与`&&` 两边均为真即是真
- 或`||` 两边有一个真及,即是真
- 非`!` 取反,真为假,假为真

js中为假的值
1. null
2. undefined
3. 数字0
4. ''(空字符串)
5. NaN

## 三元运算符

`var re = (a>b)?'true':'false';`





