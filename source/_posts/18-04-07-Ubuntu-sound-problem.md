---
layout: post
title: 关于Ubuntu没有声音的解决方法
date: 2018-04-07 05:20:44
comments: true
tags:
    - Ubuntu
    - 坑
categories:
    - 笔记
---

![sound](https://ws1.sinaimg.cn/large/006tNbRwly1fwbm6111f5j30jv0byaby.jpg)

### 关于Ubuntu没有声音的解决方法

<!-- more -->

<center>最近发现网易云客户端的Linux版本于是满心欢喜的下载安装试了试</center>

<center>但是 突然发现系统<big>没有声音了</big>！！！！</center>

<center>小鱼那个心里苦啊～～～～    ╮(╯▽╰)╭    </center>

<center>没办法自己造的罪还需自己去解决！</center>

<center>不能轻言放弃！</center>

<center>经过一番搜索 找到了一个不错的解决方案</center>

### 命令

``` bash
$ aplay -l
```
### 检查输出

``` bash
$ alsamixer
```
### 将所有选项调高（warning：不要调到最大，可能会被Surprise）
``` bash
$ sudo killall pulseaudio
```
### 然后<big>注销</big>一下  问题解决！
<center>希望这个操作会对你有用</center>


---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---