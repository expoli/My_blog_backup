---
layout: post
title: 新建大文件以制作loop设备文件来克服分区不良
date: 2018-07-15 09:26:08
comments: true
tags:
    - Centos7
    - Linux 分区
categories:
    - 笔记
---

![Centsos](https://ws2.sinaimg.cn/large/006tNbRwly1fwblaknkmuj30go08rgm6.jpg)

### 分区的重要性

<!-- more -->

* 服务器的合理分区，有很多的时候都是个很头疼的问题，我们一开始进行的分割是一开始的需求，但是随着使用时间的增加很多时候我们会发现我们一开始的分区方案无法满足我们现在的需求，这个时候，如果我们制作一个 **大文件**，然后将这个文件 **格式化 挂载** ，这个有趣的操作能够帮助我们解决很多系统分区不良的情况。

* 举例来说，如果你在分区的时候只分出了一个根分区，假设你已经没有多余的空间进行额外的分区，而你的根分区又很大这个时候，制作一个大文件然后挂载上去，这样你就多了一个分区，用途很广泛！ 仔细一想，简直是 **神器** ！

### 操作命令

```bash
# 首先创建大文件
# dd if=/dev/zero of=/home/loopdev bs=1M count=512		# 向文件中写入512MB的0

# 格式化
# mkfs -t ext4 /home/loopdev	# 这里会提示你这不是正常的设备选 是

# 挂载
# mount -o loop /home/loopdev /www/data

# df -H		# 具体查看一下 成果
```


---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---