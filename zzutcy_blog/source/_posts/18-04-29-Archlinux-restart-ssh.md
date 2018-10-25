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

![Arch and ssh](https://ws3.sinaimg.cn/large/006tNbRwly1fwblvf9pcej30ci0cijrt.jpg)

### Archlinux开启ssh服务命令

<!-- more -->

```bash
# systemctl enable sshd.service     开机启动

# systemctl start sshd.service      立即启动

# systemctl restart sshd.service    立即重启
```

**之后你就可以远程操控你心爱的 linux 了 是不是很激动啊！**


---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---