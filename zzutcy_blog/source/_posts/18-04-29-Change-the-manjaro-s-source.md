---
layout: post
title: Arch 优秀衍生版 manjaro 设置国内源
date: 2018-04-29 09:35:34
comments: true
tags:
    - Manjaro
categories:
    - 笔记
---

![Manjaro](https://ws1.sinaimg.cn/large/006tNbRwly1fwblya1eb9j30qo0csdhf.jpg)

### 设置官方镜像源（包括 core， extra， community， multilib ）

<!-- more -->

```bash
$ sudo pacman-mirrors -i -c China -m rank //更新镜像排名
```

然后勾选你需要的镜像源，确认即可。

```bash
$ sudo pacman -Syy //更新数据源
```

** OK! 完成！ 真的很方便！ manjaro 真是一个优秀的发行版，但是为什么国内用的人这么少呢？ 不太理解，毕竟中文支持也很棒，用户体验也一流。推荐试用哈！**


---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---