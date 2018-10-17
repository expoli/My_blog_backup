---
layout: post
title: Linux 关机的正确姿势
date: 2018-04-27 08:24:19
comments: true
tags:
    - Linux
    - 维护
categories:
    - 笔记
---

![Dont shut down my pc](https://ws1.sinaimg.cn/large/006tNbRwly1fwbmehiunyj30dw08paa3.jpg)

### Linux命令sync强制将内存中的文件缓冲内容写到磁盘

sync用于强制将内存中的文件缓冲内容写到磁盘。linux系统为了提高读写磁盘的效率（buffer：为了解决写磁盘的效率。cache：为了解决读磁盘的效率），会先将
<!-- more -->
数据放在一块buffer中。在写磁盘时并不是立即将数据写到磁盘中，而是先写入这块buffer中了。

在系统关机或者重启时，会自动把缓冲区的内容自动同步到磁盘中，但是如果系统异常关机，会有缓存文件丢失的情况。因此，我们也可以手工去执行sync命令，强制将内存中的文件缓冲内容写到磁盘。

### 命令分类：磁盘目录管理

### 语法格式

``` bash
$ sync [选项]
```

### 参数

```
--help：显示此帮助信息并退出
--version：显示版本信息并退出
```


### 示例
将缓存内容写入到磁盘中 并且 重启

``` bash
# sync;sync;sync; reboot
```

**在这里为了让缓存都写入到磁盘中用了 3 次指令 以防万一 !!**

