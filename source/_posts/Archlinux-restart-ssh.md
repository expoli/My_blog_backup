---
layout: post
title: Archlinux开启ssh服务以使用终端登录
date: 2018-04-29 08:40:29
comments: true
tags:
    - Arch
    - ssh
categories:
    - 笔记
---

![Arch and ssh](https://s1.ax1x.com/2018/10/12/iNizjI.png)

### Archlinux开启ssh服务命令

<!-- more -->

```bash
# systemctl enable sshd.service     开机启动

# systemctl start sshd.service      立即启动

# systemctl restart sshd.service    立即重启
```

**之后你就可以远程操控你心爱的 linux 了 是不是很激动啊！**
