---
layout: post
title: Ubuntu 安装 nginx
date: 2018-04-16 22:21:39
comments: true
tags:
    - Ubuntu
    - Nginx
categories:
    - 笔记
---

![Ubuntu and nginx](https://ws2.sinaimg.cn/large/006tNbRwly1fwbm6k5jtdj30lb0c0t9t.jpg)

### 命令操作

<!-- more -->

``` bash
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install nginx
```

初次安装会自动要求安装一堆的依赖，接受并安装即可。

Nginx 会自动安装为服务并开机自启。

### 安装验证

从浏览器输入自己的公网IP（或者是指向该IP的域名）即可验证是否安装成功。

正常情况会看到如下Nginx欢迎页
![image956f44210618f766.png](https://tc.zzutcy.top/images/2018/10/20/image956f44210618f766.png)

### 嗯！就是这么简单粗暴！哈哈哈

跑起来个样例站简单，但配置实际上很有学问可讲，玩法很多。
