---
layout: post
title: 更改Ubuntu软件镜像源
date: 2018-04-20 07:38:45
comments: true
tags:
    - Ubuntu
categories:
    - 笔记
---

![Ubuntu sources](https://ws1.sinaimg.cn/large/006tNbRwly1fwblytqr62j311y0lc44f.jpg)

Ubuntu 的软件源配置文件是 

<!-- more -->

```bash
/etc/apt/sources.list
```

将系统自带的该文件做个 **备份** 将该文件替换为下面内容，即可使用 **TUNA （清华大学开源软件镜像站）**的软件源镜像。

我的Ubuntu版本是`16.04 LTS`

### 对应的配置文件如下
```bash
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted universe multiverse# 预发布软件源，不建议启用
# deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-proposed main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-proposed main restricted universe multiverse
```

[其它Ubuntu版本](https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/)


---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---