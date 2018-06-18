---
layout:     post
title:      "php错误与异常 "
subtitle:   "errors and execption"
date:       2018-06-13 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - php
---

## 异常

异常是Exception类的对象，在遇到无法修复的状况时抛出，实例化时可传入两个参数,分别是提示消息与数字代码，数字代码不是必须的。

```
//抛出异常示例
throw new Exception('An unexpected problem');
```

### try/catch捕获异常

```
try{
	throw new Execption('An unexpected problem');
}catch(Exception $e){
	echo 'error:'.$e->getMessage();
}finally{
	//这里的代码最后都会执行
}
```

### Exception类

PHP有很多异常处理类,Execption类是所有异常处理类的基类。Exception类有几个基本的属性和方法，其中属性包括：

- message 异常消息内容
- code 异常代码
- file 抛出异常的文件名
- line 抛出异常的所在行数

常用的方法有：

- getTrace 获取异常追踪信息
- getTraceAsString 获取异常追踪信息的字符串形式
- getMessage 获取出错的信息

如果有需要可以通过继承Exception类来建立自定义异常处理类

```
class ProException extends Exception {
	function selfInfo() {
		return '自定义信息';
	}
}
```

### 将捕获的异常信息存入到错误日志

```
try {
	throw new Execption('A new problem');
}catch(Execption $e) {
	//异常消息内容
	$errormsg = 'Error'.$e->getMessage()."\n";
	//异常追踪信息
	$errormsg .= 'Trace'.$e->getTraceAsString()."\n";
	//异常行号
	$errormsg .= 'Line'.$e->getLine()."\n";
	//异常文件
	$errormsg .= 'File'.$e->getFile()."\n";
	//将异常信息写入日志
	file_put_contents('error.log',$errormsg);
}
```

### 全局异常处理程序

全局异常处理程序用`set_exception_handler()`函数注册，可以用来捕获所有未被捕获的异常

```
set_exception_handler(function(Execption $e){
		//处理异常代码
	});
throw new Exception('An unexpected problem')
```

## 错误

可以使用`error_reporting()`函数或者在php.ini文件中使用errorreporting指令告诉PHP报告或者忽略那些错误。这两种都是使用`E*`常量来确定

生产环境和开发环境应该用不同的配置，在开发环境直接显示错误，生成环境不显示错误，但是都需要报告错误和记录错误。

### php.ini 配置 

需要修改`php.ini`来达到我们的需求，yum安装的话，文件位置应该在`/etc/php.ini`

开发环境配置:

```
;显示错误
display_startup_errors = On
display_errors = On
;向PHP报告发生的每个错误
error_reporting = E_All
;开启错误日志
log_errors = On
;设置每条日志项的最大长度(可以不设置)
log_errors_max_len = 1024
;错误日志位置
errors_log = /var/php_errors.log
```

生产环境配置：

```
;显示错误
display_startup_errors = Off
display_errors = Off 
;除提示外,向PHP报告发生的每个错误
error_reporting = E_All & ~E_NOTICE
;开启错误日志
log_errors = On
;设置每条日志项的最大长度(可以不设置)
log_errors_max_len = 1024
;错误日志位置
errors_log = /var/php_errors.log
```

### 全局错误处理程序

全局错误处理程序需要用`set_error_handler()`函数进行注册

```
//回调函数处理出现的错误，函数的参数:错误级别、错误信息、错误文件、错误所在行
set_error_handler(function($severity, $message, $file, $line) {
	throw new \ErrorException($message, 0, $severity, $file, $line);
});
```
