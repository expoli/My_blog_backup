---
layout: post
title: 讲一下在给服务器装系统时遇到的坑
date: 2018-04-20 08:34:26
comments: true
tags: 
    - 坑
categories: 
    - 笔记
---

![Server](https://ws4.sinaimg.cn/large/006tNbRwly1fwbm4jpma0j30zk0mmdm0.jpg)

## 讲一下在给服务器装系统时遇到的坑

<!-- more -->

因为第一次接触服务器，所以不太清楚服务器的机器的特性，看到机器预装的是win server 2008、又看到机器说明书上所说支持CentOS 于是，就准备给机子换个“身体”，给他装上Linux。。。

于是经过一番漫长的下载，写入，，等待，，，，终于！！！ 进入了安装界面！！ 激动人心的时刻到来了。

神圣的按下确定 突然！！！ WTF error？？？？
（¥×`===¢「=√¢^¥^¢√）你能想像我此时的心情吗？

经过一番排查，最终发现是分区表问题 原来的分区表格式是MBR 格式 现在需要的是 GPT 格式。OK 更改分区表，一路安装，经过漫长的等待。。。安装成功！！然后 我，很憋屈的发现，，我TM不会用。。。。而且重启之后网络会自动关闭。。。而且ssh 也不能用？？？？什么鬼。果断放弃！

再见，CentOS 你与我无缘.

OK 换系统。还是用Ubuntu 吧，然后在安装的过程中我发现了一个有趣的现象，Ubuntu那所谓的高级分区工具，居然没法把CentOS的分区给删除！！！什么情况？？？

这是逼我拿出大杀器啊，祭出大杀器！PE上场！删区合并一同操作猛如虎！

然后尝试了一下Debian 经过一番长久的等待 安装完成 然后突然发现 出现了 请插入 CD-ROM 的报错！！

？？？？什么鬼。经过搜索 发现是软件源的问题。把相关信息 注释掉 可以使用了。 但是因为软件源和支持问题 最后又改为了 Ubuntu 。。。。。

这波操作。。。我很服。。。


---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---