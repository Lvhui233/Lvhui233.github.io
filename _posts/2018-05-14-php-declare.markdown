---
layout:     post
title:      "流程控制 "
subtitle:   "declare"
date:       2018-05-14 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - php
---

## declare

declare目前只人数两个指令,ticks与encoding

### Ticks

Tick（时钟周期）是一个在 declare 代码段中解释器每执行 N 条可计时的低级语句就会发生的事件。N 的值是在 declare 中的 directive 部分用 ticks=N 来指定的

不是所有语句都可计时。通常条件表达式和参数表达式都不可计时。

在每个 tick 中出现的事件是由 register_tick_function() 来指定的。

```
<?php
function DoTicks (){
	echo 'Ticks';
} 
register_tick_function('DoTicks');
declare(ticks = 1) {
	for($x = 1; $x < 10; ++ $x){
		echo $x*$x . '<br/>';
	}
}
?>
```

运算结果

```
1
TicksTicks4
TicksTicks9
TicksTicks16
TicksTicks25
TicksTicks36
TicksTicks49
TicksTicks64
TicksTicks81
TicksTicksTicksTicks
```

每执行完一条语句就会触发一次ticks事件

首先完整的for循环算一个语句，但必须要等循环结束才算，因此在编译时for循环里面的echo 算第一个语句。

所以第一个doTicks是在第一个echo后执行的，也就是1输出后才发生第一个tick事件。

在$x 从1到9的循环中，每个循环包括两个语句，一个echo, 一个for循环。在81输出后，因为echo是一条语句，因此输出第一个ticks。

同时$x=9的这个for循环也结束了，这又是一条语句,输出第二个ticks；开始$x=10的循环，但这时已不满足循环条件，for循环执行结束，这个循环又是一个语句，这时输出第三个ticks。

最后declare本身也算一条语句，所以又输出第四个ticks

### Encoding

可以用 encoding 指令来对每段脚本指定其编码方式

```
<?php
declare(encoding='ISO-8859-1');
// code here
?>
```

## goto

用来跳转到程序中的另一位置,只能用于同一文件和作用域,无法跳转出函数或类,也不能跳入任何循环域switch结构中.可以跳出循环或者 switch，通常的用法是用 goto 代替多层的 break

```
<?php
for($i=0,$j=50; $i<100; $i++) {
  while($j--) {
    if($j==17) goto end; 
  }  
}
echo "i = $i";
end:
echo 'j hit 17';
?>
```
