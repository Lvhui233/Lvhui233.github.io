---
layout:     post
title:      "PHP数学函数和字符串"
subtitle:   "PHP Math and string"
date:       2017-05-31 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - PHP
---

## 数学函数

```
ceil(2.3); //向上取整
floor(3.6); //向下取整
max(1,2,34,23,11); //取最大值
min(1,2,34,23,11); //取最小值
round(32.12); //四舍五入
mt_rand(1,10); //生成更好的随机数
pow(2,10); //指数表达式
```

## 字符串

### 字符串的定义

- 单引号定义
- 双引号定义，可以解析其中的变量，必要时变量用{}括起来
- 定界符定义

```
$str = <<< here
This is the content
here;
```

### 字符串处理函数

#### 去空白

```
trim($str); //去除首尾空白
ltrim($str); //去除前导空白
rtrim($str); //去除后缀空格
```

#### 获得字符串长度

```
echo mb_internal_encoding(); //显示默认编码
strlen($str); //获得字符串长度
mb_strlen($str,'utf-8'); //获得字符串长度，指定编码
```
#### 转换大小写

```
strtolower($str); //字符全变小写
strtoupper($str); //字符全变大写
```

#### 首字母大写

```
ucfirst($str); //字符串首字母大写
ucwords($str); //所有单词首字母大写
```

#### md5加密

md5是不可逆的一种加密方式，返回32字节字符串
```
md5('abc2211321');
```

#### 将字符串分割成数组

```
$arr = explode('-','lemon-apple-banana');
print_r($arr);
```

#### 将数组转成字符串

```
$arr = array('a','b','c');
$str = implode(',',$arr);
echo $str;
```

#### 截取字符串

```
substr('sasasasd',2,3); //从2号开始截取3个字符
mb_substr('秋水共长天一色',1,2,'utf-8'); //截取中文字符
```

#### 获取特点字符后的字符

```
$str = 'lvhui233.github.io';
strchr($str,'.'); //获得$str第一个.后面的内容(.github.io)
strrchr($str,'.'); //获得最后一个.后面的内容(.io)
```

#### 获得字符在字符串中的位置

```
$str = 'lvhui233.github.io';
strpos($str,'.'); //获得.在$str中第一次出现的位置
strrpos($str,'.'); //获得.在$str中最后一次出现的位置
```

#### 替换字符

```
$str = str_replace(被替换字符，新字符，被操作字符串);
$str = str_ireplace(被替换字符，新字符，被操作字符串); //不区分大小写
```

#### url编码

替换所有非字母数字的字符，变为%后面跟两位16进制数，空格变为+


```
$str = urlencode('http://lvhui233.github.io'); //进行URL编码转换
urldecode($str); //将被转换后的编码进行解析还原
```

#### html实体

```
htmlspecialchars(); //把指定特殊符号转换为实体,如`&lt`, `$gt`
```

#### 自动转义

```
addslashes(); //给",'.\等字符前添加\显示
stripslashes(); //addslashes的反函数，显示转义后的字符
```


