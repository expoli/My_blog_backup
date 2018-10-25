---
layout: post
title: Centos 7 的登陆文件的轮替设置 （logrotate）
date: 2018-07-18 09:26:08
comments: true
tags:
    - Centos7
    - 登陆文件
categories:
    - 笔记
---

![Centsos](https://ws2.sinaimg.cn/large/006tNbRwly1fwblaknkmuj30go08rgm6.jpg)

### 背景介绍

<!-- more -->

* 随着自己慢慢得深入了解Linux，越来越发现Linux的登陆文件的重要性，毕竟系统的很多重要信息都在他的记录范围，包括登陆者的部分信息。

    * 如果幻想你是一个很厉害的骇客，想利用别人的计算机干坏事，然后又不想留下自己的痕迹，那么最重要的就是走的时候把自己的 **屁股擦干净** ，首当其冲的就是我们系统的登录文件了，如果登录文件不见了，那么机主就没办法知道自己到底是被谁攻击了。

    * 针对这个问题，我们可以考虑使用文件的 **隐藏属性**，如果一个文件以 **chattr** 设置i这个属性的时候，那么这个文件 **连root都不能删除 ！而且也不能新增数据！** ，嗯。。。但是，似乎有点安全过头了。。。

    * 相对于i这个属性，**a** 这个属性比较适合我们的使用环境，如果你的登录文件如果设置了这个属性那么这个文件 **只能被增加，而不能够被删除**！我们要的就是这个属性。

    * logrotate 主要针对登录文件来进行轮替的工作，当我们将 **/var/log/messages** 加上a的属性后，那么logrotate 也没办法按计划更改登录文件了，这不是我们所要的，所以需要设置一下

### 指令操作

```bash
# vim /etc/logrotate.d/syslog
/var/log/cron
/var/log/maillog
/var/log/messages
/var/log/secure
/var/log/spooler
{
    sharedscripts   # 把无法修改的属性去掉
    prerotate
        /usr/bin/chattr -a /var/log/messages
    endscript
    missingok
    sharedscripts
    postrotate
    	/bin/kill -HUP `cat /var/run/syslogd.pid 2> /dev/null` 2> /dev/null || true
        /usr/bin/chattr +a /var/log/messages    # 加上保护属性
    endscript
```

### 强制进行一次 logrotate 的动作
```bash
# logrotate -vf /etc/logrotate.conf
```

### 检验自己的设置是否生效
```bash
$ ll /var/log/messages*; lsattr /var/log/messages
```


---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---