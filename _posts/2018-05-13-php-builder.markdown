---
layout:     post
title:      "生成器 "
subtitle:   "builder"
date:       2018-05-13 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - php
---

## 生成器

生成器函数看起来像普通函数,当生成器函数被调用时,返回一个可以被遍历的对象,遍历这个对象时,php会在每次需要值得时候调用生成器函数

```
function getnumber(){
	for($i = 1; $i <= 3; $i++){
		//每次返回值
		yield $i;
	}
}
$generator = getnumber();
foreach($generator as $v){
	echo $v;
}

//在表达式上下文用yield要用括号
$data = (yield $v);
```

- 除了生成简单的值,生成器也支持生成键值对
- yield 在没有传参数时,会生成null值
