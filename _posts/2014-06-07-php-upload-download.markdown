---
layout:     post
title:      "PHP上传和下载"
subtitle:   "PHP upload and download"
date:       2014-06-07 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - PHP
---

## 文件下载

```
//定义要下载的文件路径
$file=$GET['path'];
//设置头信息，告诉浏览器是二进制文件
header("Content-type:application/octet-stream");
//提取文件名
$fileName = basename($file);
//设置下载框中要显示的文件名
header("Content-Disposition:attachment;filename={$fileName}");
//文件大小单位
header("Accept-ranges:bytes");
//文件大小
header("Accept-length:".filesize($file));
readfile($file);
```

## 文件上传

### 上传设置

表单中需要上传文件时，需要在form标签中添加`enctype="multipart/form-data"`

### php.ini上传文件配置项

- file_uploads=On/Off 是否允许文件上传
- upload_max_filrsize=2M 上传文件的最大大小
- post-max-size=8M POST数据所允许的最大大小
- upload_tmp_dir 上传文件放置的临时目录

### 文件上传处理(函数)

```
//判断文件是否是HTTP POST上传的合法文件
is_uploaded_file(文件路径); 
//将上传的文件移动到新位置
move_uploaded_file(临时文件位置,保存到的新位置);
```

### $FILES

上传文件一般用post方式传输,用$FILES来接收,接收到的是一个数组,
上传单个文件和多个文件时所接收到的数组形式略有不同,多文件上传
需要重新组合数组，以便之后的处理

### 单文件上传

```
uploadfile($_FILES['img']);
//用来处理上传后文件的函数，传入的参数应该是包含文件上传信息的数组
function uploadfile($arr){
//    获得后缀名
    $ext = pathinfo($arr['name'])['extension'];
//    组合移到的目的地
    $tofile = 'uploads/'.time().'.'.$ext;
    move_uploaded_file($arr['tmp_name'],$tofile);
}
```

### 多文件上传

```
//重新组合多个文件的信息
$filesarr = array();
for ($i = 0; $i <count($_FILES['up']['name']);$i++){
    $filesarr[] = array(
        'name'=>$_FILES['up']['name'][$i],
        'type'=>$_FILES['up']['type'][$i],
        'tmp_name'=>$_FILES['up']['tmp_name'][$i],
        'error'=>$_FILES['up']['error'][$i],
        'size'=>$_FILES['up']['size'][$i],
    );
}
//p($filesarr);

//循环组合后的数组，依次调用上传函数
foreach($filesarr as $k=>$v){
//    p($v);
    uploadfile($v);
}
//用来处理上传后文件的函数，传入的参数应该是包含文件上传信息的数组
function uploadfile($arr){
//    获得后缀名
    $ext = pathinfo($arr['name'])['extension'];
//    组合移到的目的地
    $tofile = 'uploads/'.time().mt_rand(1,100000000).$arr['size'].'.'.$ext;
//    p($tofile);
    move_uploaded_file($arr['tmp_name'],$tofile);
}
```

