---
layout:     post
title:      "popos解锁APT包管理"
subtitle:   "unlock package management"
date:       2018-06-03 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - ubuntu
---

## Ubuntu及其衍生版系统解锁APT包管理器

换了新笔记本之后，给之前的老本子换了新的popos系统，一段时间没有用之后,再开机系统需要更新，但是再更新过程中出现了等待包管理器解锁的问题。可能是由于网络阻塞等问题，无法正常安装，取消后dpkg被锁定，不能再安装任何其他软件包，重新启动系统依然不能解决这个问题。

下面是在网上找到的用命令行进行解锁

```
keith@pop-os:~$ sudo rm -rf /var/lib/dpkg/lock   # 先删除锁定 

sudo dpkg --congigure -a   # 然后重新配置
```


