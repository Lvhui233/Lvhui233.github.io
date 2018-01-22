---
layout:     post
title:      "PHP面向对象"
subtitle:   "PHP object oriented"
date:       2014-06-12 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - PHP
---


## 类

### 创建类

```
//类名首字母一般大写
class Man{
	public $action='run';
}
//用类实例化对象
$male=new Man;

### 类的继承

```
//父类
class Father{
	public $name;
	public $age;
	public $sex;
	public function say(){
		echo 'can speak';
	}
}
//子类
class Son extends Father(){
	public function say(){
		echo 'can speak,too';
	}
}

### 声明属性和方法

- `public` 可在内部外部和子类调用
- `protected` 可在内部和子类调用
- `private` 只能在内部调用，无法被子类继承

## 构造方法与析构方法

### 构造方法

在对象创建时自动执行，没有返回值，在对象创建时传进的参数，即是此函数的参数。
声明时可以用`__construct`也可以和类同名，但是前者优先，若没有前者时会找同名
的方法自动执行

```
class Add{
	public function __construct(){
		echo 'start';	
	}
}
$add=new Add(); //对象创建时自动执行
```

### 析构方法

在对象被调用完毕后执行，不带任何参数

```
class App{
	public function __destruct(){
		echo 'end';
	}
	public function run(){
	echo 'fine';
	}
}
$app = new App();
$app->run();
```

## 静态属性和静态方法

静态属性和方法属于类，不属于对象，所以无法在对象里调用，只能调用类里的变量和方法

### 声明静态变量和静态方法

```
class App{
	static public $num='233'; //静态属性
	static public function run(){
		echo 'run';  //静态方法
	}
}
```

### 静态变量和方法的调用

静态方法里无法调用类里普通的变量和方法

#### 内部调用

在普通的方法里,可以调用和修改静态方法或属性

```
class App{
	static public $num='233'; 
	static public function run(){
		echo 'run';  
	}
	public function abc(){
		//self表示调用自身类
		echo self::$num;
		self::run();
		//另一种调用方法直接调用类名
		echo App::$num;
		App::run();
	}
}
```

#### 外部调用

```
class App{
	static public $num='233'; 
	static public function run(){
		echo 'run';  
	}
}
//外部调用
echo App::$num;
App::run();
```

### 静态变量和方法的继承

```
class Father{
	static public $num='233'; 
	static public function run(){
		echo 'run';  
	}
}

class Son extends Father{
	//必须用静态方式重新声明父级中的静态变量和方法
	static public $num='111';
	static public function run(){
		echo 'stop';
	}
	//用parent调用父元素的变量和方法
	echo parent::$num;
}
```

## 魔术常量

```
__CLASS__  //返回该类被定义时的名字(区分大小写)
__METHOD__ //返回该方法被定义时的名字(区分大小写)
__DIR__  //返回脚本所在目录
__FILE__ // 返回文件的完整路径和文件名，如果用在被包含文件中，则返回被包含文件的文件名
```

## 魔术方法(拦截)

### __isset()

外部检查私有属性时，会自动调用函数

```
class Man{
	private $age='23';
	__isset($name){
		echo $name.'是私有属性';
	}
}
$man=new Man();
echo isset($man->age);
```

### __unset()

外部删除私有属性时，会自动执行

```
class Man{
	private $age='23';
	__unset($name){
		unset($this->$name);
		echo $name.'属性已删除';
	}
}
$man=new Man();
unset($man->age);
```

### __get()

获取对象未定义的属性时，自动运行的函数

```
class Man{
	private $age='23';
	__get($name){
		echo '当前类没有'.$name.'属性';
	}
}
$man=new Man();
echo $man->url;
```

### __set()

给未定义的属性赋值时，会自动执行的函数

```
class Man{
	private $age='23';
	__set($name,$value){
		$this->$name=$value;
		echo $this->name;
	}
}
$man=new Man();
$man->url='coolerk.com';
```

### __call()

调用一个未定义的方法时，自动运行的函数

```
class Man{
	private $age='23';
	__call($name,$arguments){
		echo '当前类没有'.$name.'方法';
	}
}
$man=new Man();
$man->run('123');
```

### __autoload()

如果程序中要用到某个类,但是并没有找到已经引入的该类,那么
就会触发__autoload的执行

```
function __autoload($info){
    include $info.'.class.php'; //$info的值就是类名
}

//自动加载
$obj = new User();
$obj->foo();
```

## 抽象类&抽象方法

父类为抽象类时，子类必须重写父类的抽象方法。
抽象类里不一定非要有抽象方法，但抽象方法必须在抽象类里才能定义
抽象类必须继承使用
抽象方法不能有主体即{}

```
abstract class Animal{
	abstrsct public function color($var);
}
class Fish extends Animal{
	public function color($var){
		echo $var;
	}
}
$sharp = new Fish();
$sharp->color('white and blue');
```

## 相关函数

### get_class_methods()

返回由类的方法名组成的数组

### get_class_vars()

返回由类的默认属性组成的关联数组(private与protected属性无法获得)

### get_object_vars()

返回由对象属性组成的关联数组

### call_user_func_array()

调用回调函数，并把一个数组参数作为回调函数的参数
`call_user_func_array(array(对象,对象里的方法),array(参数1，参数2))`

### method exist

检测类的方法是否存在

```
method exist(类,方法);
```










