---
layout:     post
title:      "linux下lnmp环境搭建 "
subtitle:   "lnmp build on linux"
date:       2018-05-30 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - lnmp
---

## 服务器环境

centos7.4

## 修改yum源

### nginx源

```
[root@izi5l7x6yg6c17z ~]# rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```

### php源

```
[root@izi5l7x6yg6c17z ~]# rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
```

### mysql源

```
[root@izi5l7x6yg6c17z ~]# rpm -Uvh http://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm
```

php源:Webtatic[https://webtatic.com](https://webtatic.com)
mysql源:[https://dev.mysql.com/downloads/repo/yum/](https://dev.mysql.com/downloads/repo/yum/)

## 安装

### 安装nginx

```
[root@izi5l7x6yg6c17z ~]# yum -y install nginx
```

### 安装mysql

```
[root@izi5l7x6yg6c17z ~]# yum -y install mysql-community-server
```

### 安装php

```
[root@izi5l7x6yg6c17z ~]# yum -y install php72w-devel php72w-cli.x86_64 php72w-common.x86_64 php72w-gd.x86_64 php72w-ldap.x86_64 php72w-mbstring.x86_64  php72w-pdo.x86_64   php72w-mysqlnd  php72w-fpm php72w-opcache php72w-pecl-redis php72w-pecl-mongodb
```

## 配置

### 配置mysql

#### 修改默认密码

mysql按住能够完成后，会在`/var/log/mysqld.log`文件中给root用户生成默认密码，通过以下方式查找默认密码并修改，
默认密码登录后不能进行其他操作，必须先设置新密码

查看默认密码：

```
[root@izi5l7x6yg6c17z ~]# systemctl start mysqld    # 启动MySQL
[root@izi5l7x6yg6c17z ~]# grep 'temporary password' /var/log/mysqld.log  # 查找默认密码
2018-05-29T02:58:16.806931Z 1 [Note] A temporary password is generated for root@localhost: iacFXpWt-6gJ
```

登录mysql：

```
[root@izi5l7x6yg6c17z ~]# mysql -uroot -piacFXpWt-6gJ
```

设置新密码：

```
set password = password('Abc123*');
```

密码要求包含数字 小写字母 大写字母 特殊字符 而且长度至少8位

#### 配置默认编码utf8

修改`/etc/my.cnf`配置文件

```
[root@izi5l7x6yg6c17z ~]# vim /etc/my.cnf
```

在`[mysqld]`最后添加以下代码

```
character_set_server=utf8
init_connect='SET NAMES utf8'
```

重启myslq

```
[root@izi5l7x6yg6c17z ~]# systemctl restart mysqld
```

设置开机自启

```
[root@izi5l7x6yg6c17z ~]# systemctl enable mysqld
```

#### MySQL默认配置文件路径

配置文件：`/etc/my.cnf`
日志文件：`/var/log/mysqld.log`
服务启动脚本：`/usr/lib/systemd/system/mysqld.service`
socket 文件：`/var/run/mysqld/mysqld.pid`

### 配置nginx

#### 防火墙配置

查看防火墙是否开启：

```
[root@izi5l7x6yg6c17z ~]# systemctl status firewalld
```

如果显示`Active: inactive (dead)`说明防火墙没有开启，如果显示`Active: active (running)`，则需要调整防火墙规则的配置。

修改`/etc/firewalld/zones/public.xml`文件，在zone一节中增加
保存后重新加载 firewalld 服务：

```
[root@izi5l7x6yg6c17z ~]# vim /etc/firewalld/zones/public.xml
<zone>
    ...
    <service name="nginx"/>
<zone>
[root@izi5l7x6yg6c17z ~]# systemctl reload firewalld
```

#### 修改nginx配置

```
[root@izi5l7x6yg6c17z ~]# vim /etc/nginx/nginx.conf
```

在`server {}`里添加：

```
location / {
    #定义首页索引文件的名称
    index index.php index.html index.htm;   
}

# PHP 脚本请求全部转发到 FastCGI处理. 使用FastCGI默认配置.
location ~ .php$ {
    fastcgi_pass 127.0.0.1:9000;
    fastcgi_index index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    include fastcgi_params;
}
```

开启nginx服务:

```
[root@izi5l7x6yg6c17z ~]# systemctl start nginx
```

开启服务时可能报以下错误`Job for nginx.service failed because the control process exited with error code. See "systemctl status nginx.service" and "journalctl -xe" for details.`

`检查配置末尾是否都加了';'分号`

开机启动：

```
[root@izi5l7x6yg6c17z ~]# systemctl enable nginx
```

#### 启动php-fpm

```
[root@izi5l7x6yg6c17z ~]# systemctl start php-fpm
[root@izi5l7x6yg6c17z ~]# systemctl enable php-fpm
```

## 测试

- 在`/usr/share/nginx/html`文件下创建php文件，输出 phpinfo 信息

- 浏览器访问 http://IP地址/phpinfo.php，如果看到 PHP信息，说明安装成功
