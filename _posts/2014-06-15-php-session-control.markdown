---
layout:     post
title:      "PHP会话控制"
subtitle:   "PHP session control"
date:       2014-06-15 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - PHP
---

## cookie

cookie储存在客户端，如果不设置保存时间，会在浏览器关掉的时候
就自动清理掉，大小一般在4kb左右,每一个浏览器独立保存

```
//生成cookie
setcookie(名字,值,过期时间,服务器端有效路径);
setcookie('webbname','coolerk',time()+3600*24*7,'/');
```

### cookie存储数组或对象

通过序列化来实现

```
//序列化数组
$arr=serialize(array(1,2,3,4));
setcookie('num',$arr);
//反序列化
unserialize($arr);

```

## session

在开始会话的时候，会分配给用户一个sessionID，用来标识当前
用户，与其他用户进行区分

### 开启会话

`session_start()`执行时会搜索客户端有无session_id,如果有会
根据session_id找到session数据,如果没有将在服务器写入SESSION
文件，并在客户端存入对应的session_id

```
session_start();
//存入信息
$SESSION['num']=1;
//获取信息
$a=$SESSION['num'];
```

### session_id相关信息

```
//获取设置session_id
session_id();
//获取设置session_name
session_name();
延长session_id在cookie在客户端存储时间
session_start();
setcookie(session_name(),session_id(),time()+3600*24*7,'/');
```

### 清除session

```
//删除session变量
unset($SESSION('name'));
//删除所有session变量，不删除session文件
$SESSION=array();
//释放当前内存中创建的所有session变量,但不删除session文件和session_id
session_unset();
//删除当前用户对应的session文件，释放session_id,但不删除session变量内容
session_destroy();
//释放用户的所有资源
session_unset();
session_destroy();
```

### 更改session保存路径

会话数据的路径,如果指定路径,将数据保存到路径中

```
session_save_path();
```

