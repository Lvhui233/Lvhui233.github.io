---
layout:     post
title:      "项目放到服务器上时的注意事项 "
subtitle:   "Some precsutions while putting projects on the server"
date:       2018-06-10 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - lnmp
---

代码上传到服务器时，涉及到权限，配置等的设置

## 框架文件权限设置

```
chmod -R 777 boostrap
chmod -R 777 storage
```

## 修改nginx默认web路径

修改配置文件，所在路径为`/etc/nginx/nginx.conf`,修改serve下的root

```
server {
        listen       80 default_server; 
        listen       [::]:80 default_server;
        server_name  _;
        root         /usr/share/nginx/html;

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

        location / {
            index index.php index.html index.htm;
        }

        location ~ .php$ {
            fastcgi_pass 127.0.0.1:9000;
            fastcgi_index index.php;
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            include fastcgi_params;
        }

        error_page 404 /404.html;
            location = /40x.html {
        }

        error_page 500 502 503 504 /50x.html;
            location = /50x.html {
        }
    }
```

修改配置之后重启nginx

```
nginx -s reload
```

## github拉取部署时注意事项

我们在上传代码时都会在`.gitignore`里记录让git忽略上传的文件,如依赖文件`vendor`文件以及配置文件`.env`等，所以如果在服务器上直接拉取代码记得执行重新执行`composer install`

```
# 拷贝远端文件
git clone https://github.com/laravel/laravel.git
# 进入到项目文件执行生成vendor文件解决依赖问题
composer install
# 更新compser
composer update
# 建立.env文件
cp .env.example .env
# env.example中默认没有app key,所以我们在.env中生成新的app key
php artisan key:generate
# 修改.env中的配置项
vim .env
# 执行数据迁移
php artisan migrate
# 执行数据填充
php artisan db:seed
```

数据库中非数据填充生成的数据任然需要手动进行拷贝


