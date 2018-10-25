---
layout: post
title: Arch 安装Nginx
date: 2018-04-29 09:13:49
comments: true
tags:
    - Arch
    - Nginx
categories:
    - 笔记
---

![Arch and Ningx](https://ws1.sinaimg.cn/large/006tNbRwly1fwblsf6dztj31040m8tbc.jpg)

### Nginx介绍

<!-- more -->

**Nginx** (读作"engine X") 由Igor Sysoev(俄罗斯)于2005年编写，是一个免费、开源、高性能的HTTP服务器和反向代理，也可以作为一个IMAP/POP3代理服务器。根据 Netcraft 的 April 2015 Web Server Survey, 现在全世界14.48%的网站使用Nginx，而Apache占38.39%。**Nginx因为稳定，丰富的功能集，配置简单，资源占用低而闻名世界。 **

### 安装位于官方仓库的nginx 软件包。 


```bash
$ sudo pacman -Syy      //更新软件数据库
$ sudo pacman -Syu      //全面更新软件
$ sudo pacman -S nginx  //安装Nginx
```
### 启动服务

要启动Nginx服务,运行以下命令: 
```bash
# systemctl start nginx
```

### 要Nginx服务开机时启动,运行以下命令:
```bash
# systemctl enable nginx
```

http://127.0.0.1 的默认页面是:
```bash
/usr/share/nginx/html/index.html
```

### 安装验证

从浏览器输入自己的公网IP（或者是指向该IP的域名）即可验证是否安装成功。

正常情况会看到如下Nginx欢迎页
![image956f44210618f766.png](https://tc.zzutcy.top/images/2018/10/20/image956f44210618f766.png)


### 配置
你可以修改在 **/etc/nginx/** 目录中的文件来更改配置 **./etc/nginx/nginx.conf** 是主配置文件、配置完成后运行

```bash
$ sudo nginx -s reload 
```

重启nginx 使配置文件生效

[参考］("https://wiki.archlinux.org/index.php/Nginx_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)")


---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---