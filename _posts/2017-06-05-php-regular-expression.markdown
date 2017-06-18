---
layout:     post
title:      "PHP正则表达式"
subtitle:   "PHP regular expression"
date:       2017-06-05 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - PHP
---

## 元子符(原子)

- `\d` 匹配任意一个数字  //[0-9]
- `\D` 匹配任意一个非数字 //[^0-9]
- `\w` 匹配任意数字,字母,或下划线 //[0-9a-zA-z_]
- `\W` 匹配任意一个非数字,字母,下划线 //[^0-9a-zA-z_]
- `\s` 匹配任意空白字符 //[\n\f\r\t\v]
- `\S` 匹配任意非空白字符 //[^\n\f\r\t\v]
- `\n` 换行符
- `\t` 制表符

## 元字符表(原子表)

- `.` 表示除换行符外任意字符
- `[\da]` 方括号元字符表，匹配元字符表里的任意字符则表示正则通过

## 元字符组(原子组)

若一次匹配多个原子，则需要用到原子组。和原子表的区别在于，原子表一次只能匹配
一个字符，而原子组可以匹配多个

```
$preg=/(amazon|google)/;  //其中`|`表示选择修饰符，其中一个符合就通过
$str='amazon.com';
$new =preg_replace($preg,'coolerk',$str);
```

## 重复匹配

- `*` 重复零次或更多次
- `+` 重复一次或更多次
- `?` 重复零次或一次
- `{n}` 重复n次
- `{n,}` 重复n次或更多次
- `{n,m}` 重复n到m次

## 禁止贪婪

正则表达式默认匹配更多的字符，需要用`?`禁止贪婪模式，这样将会匹配尽量少的字符

## 匹配字符边界

- `^`匹配字符串的开始
- `$`匹配字符串结束，忽略换行符

## 模式修正符

- `i`不区分大小写
- `s`将字符串视为单行，使`.`可以匹配任意字符
- `e`将替换的字符作为表达式使用

```
preg = '/密码是(\d+?)/e'; 
$str = "密码是123456";
$re = preg_replace($preg,'md5(\1)',$str); //`\1`表示被替换的原字符，表示在`md5()`括号中的内容
p($re);
```

## 常用的正则操作函数

### preg_match

根据正则规则，匹配字符串中是否有所找的字符，成功匹配返回true

```
preg_match('正则规则','需要匹配的字符串');
```

### preg_match_all

将成功匹配到的所有字符以数组的形式存在`$match`中，规则中如果用了原子组，匹配到的
原子组里的字符串会被整理成一个数组存在`$match`中，即`$match[1]`

```
preg_match_all('规则','需要匹配的字符串',$match); 
```

### preg_split

通过一个正则表达式，分割字符串

```
$preg = '/[@#]/';
$str = "12.jpg@333.gif#55555.png#1111.bmp";
$re = preg_split($preg,$str);
p($re);
```

### preg_replace

执行一个正则表达式的搜索和替换

```
preg_replace('规则','替换内容','需要匹配的字符串');
```

### preg_replace_callback

执行一个正则表达式搜索并且使用一个回调函数替换

```
$str = '666';
$preg = '/\d/';
//用preg去匹配str里的内容，每个被匹配到的内容都会调用foo函数，foo函数的返回值会
将当前匹配到的内容替换掉
$result = preg_replace_callback($preg,'foo',$str);
p($result);
function foo($x){
    return '*';
//    return $x[0]+1;
```





 