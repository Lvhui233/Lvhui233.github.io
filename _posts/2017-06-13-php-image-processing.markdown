---
layout:     post
title:      "PHP面图像处理"
subtitle:   "PHP image processing"
date:       2017-06-13 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - PHP
---

## 检测拓展库是否加载

```
$a = extension_loaded('GD');
var_dump($a);
```
## 指定传输的文件类型

```
header('content-type:image/png');
header('content-type:image/jpeg');
header('content-type:image/gif');
```

## 画布

```
//创建画布
$image = imagecreatetruecolor(600,500);
//设置颜色
$red = imagecolorallocate($image,255,0,0);
//hexdec是用来将十六进制值转成十进制
$black = imagecolorallocate($image,0,0,hexdec(#000000));
//填充颜色，不填充默认黑色
imagefill($image,0,0,$red);
//绘制空心矩形
imagerectangle($image,20,20,580,480,$yellow);
//绘制实心矩形
imagefilledrectangle($image,40,40,560,460,$yellow);
//绘制空心圆形
imageellipse($image,300,250,300,200,$green);
//绘制实心圆形
imagefilledellipse($image,300,250,100,100,$black);
//画线
imageline($image,0,0,600,500,$black);
/绘制像素点
imagesetpixel($image,100,100,$red);
//写入文字
imagettftext($image,40,0,100,200,$red,'font.ttf','hello');
//输出(第二个可选参数，写的话会存入图像)
imagepng($image);
//释放资源
imagedestroy($image);
```

## 加载外部图像

```
//加载图像
$image = imagecreatefrompng('dog.png');
//获得图片宽度
$imagewidth = imagesx($iamge);
//获得图片高度
$imageheight = imagesy($image);
//获得图片信息
print_r(getimagesize('dog.jpg'));
//图像复制
imagecopy();
//图像复制并合并带透明度
imagecopymerge();
//复制部分图像并重新定义大小
imagecopyresized();



