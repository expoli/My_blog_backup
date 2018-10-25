---
layout: post
title:  在服务器上安装Chevereto图床
date: 2018-10-20 20:41:08
comments: true
tags:
    - Centos
    - Chevereto
    - 图床
categories:
    - 笔记
---

<center> ![image19f8e6ca4e588a4f.png](https://tc.zzutcy.top/images/2018/10/20/image19f8e6ca4e588a4f.png) </center>

## 为什么要搭建图床
<!-- more -->
最近在搭建博客、在写文章的时候因为服务器资源和网络环境的问题需要所以选择使用国内图床、来加速网站的访问速度。

刚开始是使用路过图床、但是后来发现我托管在路过图床上的图片国内不能访问了、然后开始将博客使用的图片一个一个转移到微博图床`令人脱发`的操作、但是后来发现微博图床也不是很稳定、所以萌生了自建图床的念头。在这记录一下心得。

在进行一番权衡之后决定使用开源的 [Chevereto](https://github.com/Chevereto) 来搭建自己私有图床、废话少说先看效果图

![image015e3e94913b58e9.png](https://tc.zzutcy.top/images/2018/10/20/image015e3e94913b58e9.png)


总的来说外观还是很漂亮很现代的、使用也很方便、而且移动端的适配也做得非常好。

（官方demo：[https://demo.chevereto.com/](https://demo.chevereto.com/) ）

## 开始安装 Chevereto 
* Chevereto 有免费版和付费版两种版本、一般来说、免费版的已经够用了。Chevereto-Free Github 站点上面介绍了免费版和付费版的区别
 -> [Chevereto-Free 传送门](https://github.com/Chevereto/Chevereto-Free) 

## 官方Wiki提到Chevereto有如下依赖：

* Nginx / Apache 服务器
* MySQL 5.0
* PHP 5.5.0

## 我所使用的环境

* Centos 7
* Nginx 1.12
* MySQL 5.0
* PHP 7.0

## Ⅰ、安装 Nginx

* 可参考我以前的博文
    * [Arch 安装Nginx](http://zzutcy.top/2018/04/28/18-04-29-Arch-install-Nginx/)
    * [Ubuntu 安装 nginx](http://zzutcy.top/2018/04/16/18-04-16-Ubuntu-install-nginx/)

## Ⅱ、安装 Mysql 

[Centos 7 安装 MySQL 教程传送门](https://www.jianshu.com/p/7cccdaa2d177)

## III、安装 PHP 7

[CentOS 7 安装 PHP 7 教程传送门](https://www.jianshu.com/p/6d3b688cd0be)

## IV.安装 Chevereto 图床

软件安装很简单，去 **Github** **项目页上看看就好**，有着官方介绍、网上教程也不少，主要提一下安装中可能遇到的几个问题以备后用。

[Chevereto-Free 传送门](https://github.com/Chevereto/Chevereto-Free)

### Clevereto 安装权限
* 若使用官方安装脚本 `index.php` 需要很高的文件权限，记得设置成 **777**。

### 提示找不到 `settings.php` 文件

* 在 `Chevereto-Free` 的 `app` 目录下面新建一个 `settings.php` 空白文件

### Clevereto 错误404解决办法
* 如果服务器是 **Nginx**，**基本第一步安装好后再次打开网站会出现404错误**。

* ### 新方案
    * 在 **location** 下写一条 **index** **index.php**; 就可以指定执行 index.php 了，使用 `rewrite` **老方案会拖慢响应速度的**，不建议

```bash
location ~ .*\.(gif|jpg|jpeg|png|bmp|swf)$
    {
        expires      30d;
        error_log off;
        access_log off;
    }
    
    location ~ .*\.(js|css)?$
    {
        expires      12h;
        error_log off;
        access_log off; 
    }
    
    #Chevereto: Pretty URLs
location / {
	index index.php;
	try_files $uri $uri/ /index.php?$query_string;
}
```


* ### 老方案：设置以下Rewrite 伪静态规则

```bash
location / {
            if (-f $request_filename/index.html){
                rewrite (.*) $1/index.html break;
            }
            if (-f $request_filename/index.php){
                rewrite (.*) $1/index.php;
            }
            if (!-f $request_filename){
                rewrite (.*) /index.php;
            }
            try_files $uri $uri/ /api.php;
        }

        location /admin {
            try_files $uri /admin/index.php?$args;
        }
```

---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---