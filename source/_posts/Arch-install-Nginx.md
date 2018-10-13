---
title: Arch 安装Nginx
date: 2018-04-29 09:13:49
cover: https://s1.ax1x.com/2018/10/12/iNiHHK.jpg
tags:
- Arch
- nginx
categories:
- 笔记
---

## Nginx介绍
**Nginx** (读作"engine X") 由Igor Sysoev(俄罗斯)于2005年编写，是一个免费、开源、高性能的HTTP服务器和反向代理，也可以作为一个IMAP/POP3代理服务器。根据 Netcraft 的 April 2015 Web Server Survey, 现在全世界14.48%的网站使用Nginx，而Apache占38.39%。**Nginx因为稳定，丰富的功能集，配置简单，资源占用低而闻名世界。 **

### 安装位于官方仓库的nginx 软件包。 
```bash
# 安装位于官方仓库的nginx 软件包。 
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
### 配置
你可以修改在 **/etc/nginx/** 目录中的文件来更改配置 **./etc/nginx/nginx.conf** 是主配置文件

[参考文献］("https://wiki.archlinux.org/index.php/Nginx_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)")
