---
layout:     post
title:      "PHP composer "
subtitle:   "PHP composer"
date:       2014-06-27 12:00:00
author:     "LvI"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog: true
tags:
    - PHP
---

## 更改环境变量

此电脑右键->高级系统设置->高级->环境变量
在系统变量中找到Path,然后编辑，win7直接将php所在
文件路径复制到最后,注意要加在前面加分号。
win10直接新建，粘贴路径，然后一直确定即可

## 下载安装 composer

浏览器搜索composer,下载后双击安装,配置好环境变量时会自动识别
文件夹.若有问题可以打开配置文件php.ini将提示的服务打开,将前
方的分号去掉即可

## 初始化 composer

在项目文件夹打开命令行,输入`composer init`命令
然后按照提示选择配置,最后后会生成composer.json

## 安装 composer

```
composer install
```

## 配置自动加载

在composer.json中加入自动加载项,然后运行`composer dump`
需要单入口引入vendor文件夹下的autoload.php文件

```
"autoload":{
        "files":[
            "system/config/database.php"
        ],
        "psr-4":{
            "houdunwang\\":"houdunwang\\",
            "app\\":"app",
            "system\\":"system\\"
        }
    }
```

