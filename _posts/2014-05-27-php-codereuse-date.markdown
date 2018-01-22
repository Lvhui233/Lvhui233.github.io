---
layout:     post
title:      "PHP代码重用和日期"
subtitle:   "PHP code reuse and date"
date:       2014-05-27 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - PHP
---


## 代码重用

`include()`和`require()`将文件导入，就像将文件粘贴到函数使用的地方，区别是当脚本出现执行失败时，`include()`会警告并继续执行，而`require()`会导致致命错误，不会再执行之后的代码。

`include_once()`和`require_once()`,如果该段代码已经被包括了便不会再执行函数

## 日期与时间

### php设定时区

php.ini配置

- 更改date.timezone = PRC

脚本中修改

- `date_default_timezone_set()` 设定当前使用时区
- `date_default_timezone_get()` 获得当前使用时区

### 时间处理函数

#### 格式化时间

```
date('y-m-d'); //格式化当前时间(字符串)
date('y/m/d','1490854781'); //格式化指定时间戳(字符串)
```

#### 获得时间戳

```
time(); //返回当前时间戳
microtime(true); //返回当前时间戳和微妙数
```

#### strtotime()

将任何英文文本描述的日期转换为时间戳

```
$time = strtotime('-1 day');
echo date('y-m-d',$time);
```

#### 取得日期/时间信息

```
$time = time();
print_r(getdate($time));
```
