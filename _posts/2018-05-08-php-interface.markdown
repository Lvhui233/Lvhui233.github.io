---
layout:     post
title:      "类常量与接口"
subtitle:   "class constants and interface"
date:       2018-05-08 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - php
---

## 类常量

用const关键字定义,值不能被改变,页可以在接口定义

```
class NewClass{
	//定义类常量
	const constant = 'constant value'; 
}
//调用类常量
echo NewClass::constant;

$newclass = new NewClass;
echo $newclass::constant;
```

## 对象接口

使用接口,可以指定某个类必须实现哪些方法,但不需要定义这些方法的具体内容,接口也可以继承，支持继承多个接口

```
//定义接口
interface project{
	public function setVariable($name, $var);
    public function getHtml($template);
}
//实现接口用implements关键字
class Newclass implements project{
	private $vars = array();
  
    public function setVariable($name, $var)
    {
        $this->vars[$name] = $var;
    }
  
    public function getHtml($template)
    {
        foreach($this->vars as $name => $value) {
            $template = str_replace('{' . $name . '}', $value, $template);
        }
 
        return $template;
    }
}
```

## trait

php是单继承语言,但是php中提供trait来实现代码的复用

```
trait one{
    public function sayhello(){
        echo 'hello';
    }
}

class NewClass{
    use one;
}
$newclass = New NewClass;
$newclass->sayhello();
```

### 优先级

从基类继承的成员会被 trait 插入的成员所覆盖。优先顺序是来自当前类的成员覆盖了 trait 的方法，而 trait 则覆盖了被继承的方法。
类不能覆盖trait里定义的属性,否则会产生fatal error

### 引入多个trait的冲突问题

```
trait A {
    public function smallTalk() {
        echo 'a';
    }
    public function bigTalk() {
        echo 'A';
    }
}

trait B {
    public function smallTalk() {
        echo 'b';
    }
    public function bigTalk() {
        echo 'B';
    }
}

class Aliased_Talker {
    use A, B {
        //使用B中的smallTalk
        B::smallTalk insteadof A;
        A::bigTalk insteadof B;
        //为B中的bigTalk起别名
        B::bigTalk as talk;
    }
}
```
