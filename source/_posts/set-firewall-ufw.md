---
layout: post
title: Ubuntu简单设置ufw防火墙
date: 2018-04-20 08:05:06
comments: true
tags:
    - Ubuntu
    - UFW
categories:
    - 笔记
---

![UFW](https://s1.ax1x.com/2018/10/12/iNA43Q.png)

**UFW**，即**简单防火墙** (**uncomplicated firewall**)，是一个 Arch Linux、Debian 或 Ubuntu 中管理防火墙规则的前端。 

<!-- more -->

**UFW** 通过命令行使用（尽管它有可用的 GUI），它的目的是使防火墙配置简单（**即不复杂 uncomplicated**）.

**一 更新系统**

```bash
$ sudo apt-get update && sudo apt-get upgrade
```

**二 安装UFW**
```bash
$ sudo apt-get install ufw
```

**三 开启UFW**
```bash
$ sudo ufw enable
```

相应的禁用UFW
```bash
$ sudo ufw disable
```

**四 设置规则**
查看运行状态
```bash
$ sudo ufw status
```

设置规则
```bash
$ sudo ufw allow Port
```

删除规则
```bash
$ sudo ufw delete allow Port
```

启用日志记录
```bash
$ sudo ufw logging on
```
日志位于
```
/var/logs/ufw
```

常规日志类似于这样

`Sep 16 15:08:14 <hostname> kernel: [UFW BLOCK] IN=eth0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=123.45.67.89 DST=987.65.43.21 LEN=40 TOS=0x00 PREC=0x00 TTL=249 ID=8475 PROTO=TCP SPT=48247 DPT=22 WINDOW=1024 RES=0x00 SYN URGP=0
`

