---
layout:     post
title:      "PHP磁盘与目录操作"
subtitle:   "PHP disk and directory"
date:       2014-06-03 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - PHP
---

## 磁盘信息

### 获得磁盘总大小

```
disk_total_space('d:'); //单位字节
```

### 获得磁盘空闲大小

```
disk_free_apsce('d:'); 
```

## 目录操作

### 获得纯文件名

```
$str ='C:/abc/text.txt'
basename($str); //获得最后一段即文件名
basename($str,'.txt'); //文件名将会去掉尾缀
```

### 获得目录路径

```
$str ='C:/abc/text.txt'
dirname($str); //返回'C:/abc'
```

### 判读文件或目录是否存在

```
$str ='C:/abc/text.txt'
file_exists($str)
```

### 检测是否为目录

```
$str ='C:/abc/text.txt'
is_dir($str);
```

### 创建目录

```
mkdir('C:/abc/text.txt',0777,true); 第一个参数时要创建的目录的路径，第二个参数代表权限，第三个参数代表递归创建
```

### 删除文件夹

```
rmdir(C:/abc/text.txt'); //文件夹必须是空的才能删除
```

### 重命名文件或文件夹

```
rename('index.php','index_bak.php'); //有返回值，返回true操作成功，返回false操作失败
```

### 复制文件

```
copy('index.php','abc/index.php'); //参数一是要复制的文件路径，参数二是复制的新文件路径
```

### 查询目录里的子文件

```
glob('abc/*'); //返回一个数组，记录abc里的所有字文件
glob('abc/*.txt'); //查找特点尾缀的文件
```
## 文件操作

### 删除文件

```
unlink('C:/abc/text.txt');
```

## 递归删除目录

```
function deldir($file){
//    判断如果文件不存在
    if (!file_exists($file)) {
        echo '文件不存在！';
        return;
    }
//    获得$file中所有的文件和文件夹
    $all = glob($file.'/*');
//    遍历处理
    foreach($all as $k=>$v){
        is_dir($v)?deldir($v):unlink($v);
    }
    rmdir($file);
}
deldir('abc');
```

## 移动目录

```
function movedir($dir,$topath){
//    如果不能存在要移动的目录，就在目标位置创建目录
    is_dir($topath.'/'.basename($dir)) || mkdir($topath.'/'.basename($dir),0777,true);
//    获得要复制的文件夹里的所有的文件
    $allfile = glob($dir.'/*');
    foreach($allfile as $k=>$v){
        if (is_dir($v)) {
            movedir($v,$topath.'/'.basename($dir));
        }else{//如果是文件，就直接复制
            copy($v,$topath.'/'.basename($dir).'/'.basename($v));
        }
    }
    rmdir($dir);
}
movedir('abc','to');
```





