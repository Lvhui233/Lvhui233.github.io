---
layout:     post
title:      "类型运算符 "
subtitle:   "instance of"
date:       2018-05-12 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - php
---
## instanceof

用来确定一个变量是否属于某一类的实例,也可以检查是不是继承自某一父类的子类的实例，以及实现了某个接口的对象的实例

```
class Myclass{

}
$a = new Myclass;
var_dump($a instanceof Myclass);
//输出 bool(true)
```


