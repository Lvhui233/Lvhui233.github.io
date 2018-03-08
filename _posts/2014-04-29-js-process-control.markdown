---
layout:     post
title:      "javascript 流程控制"
subtitle:   "javascript process control"
date:       2014-04-29 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - JS
---

##分支结构

### if else语句

```
	if(条件1){
		条件1成立执行
	}else if(条件2){
		条件2成立执行
	}else{
		以上条件皆不成立执行
	}
```

### switch语句

```
switch(变量任何的数据类型){
	case 值1:
	值1符合时执行;
	break;
	case 值2:
	值2符合时执行;
	break;
	default:
	都不符合时执行;
}
```

## 循环结构

### for循环

```
for(变量=初始值;变量<=结束值;变化值){
	循环体;
}
```

### while循环

```
while(条件){
	循环体;
}
```

### do while 循环

```
do{
	循环体
}while(条件)
```

### 循环结构中的跳转

1. break跳出并终止循环
2. continue跳出终止当前循环,如果下个值满足循环条件,继续循环
