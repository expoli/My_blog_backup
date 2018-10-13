---
layout: post
title: Arch美化——配置oh-my-zsh
date: 2018-04-29 09:01:09
comments: true
tags:
    - Arch
    - Oh my zsh
categories:
    - 笔记
---

![Arch and oh my zsh](https://s1.ax1x.com/2018/10/12/iNiqAO.png)

### ZSH 安装
```bash
$ sudo pacman -S zsh
```

<!-- more -->

### 配置默认shell：
```bash
$ sudo vim /etc/passwd
```
将要修改的用户的shell路径改为 **/usr/bin/zsh** 即可，也就是将 bash 改为 zsh

### on-my-zsh 安装
**保证安装了git ，curl (或 wget )**

```bash
$ sudo pacman -S git wget curl #curl 一般都有了，装 git wget 即可
```

```bash
$ wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh
```

```bash
$ chmod +x install.sh &&  ./install.sh
```

## **修改主题**

```bash
$ sudo vim ~/.zshrc
```

找到** ZSH_THEME="robbyrussell"**

修改为 **ZSH_THEME="random"** 为随机主题，要换其他主题，修改此处即可

修改完后打开终端即为 **on-my-zsh**(有的可能要注销一下)

&rarr;**[所有主题(https://github.com/robbyrussell/oh-my-zsh/wiki/themes)**



