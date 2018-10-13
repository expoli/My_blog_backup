---
layout: post
title: Arch 安装中文输入法
date: 2018-04-29 09:26:08
comments: true
tags:
    - Arch
    - 小狼毫
    - 推荐
categories:
    - 笔记
---

![RIME](https://s1.ax1x.com/2018/10/12/iNi2AU.png)

### 推荐安装小狼毫输入法

### 安装操作

**从官方仓库安装ibus软件包：**

```bash
# pacman -S ibus
```

此外，为了启动ibus的Qt应用程序支持, 安装ibus-qt软件库：

```
# pacman -S ibus-qt 
```

### 安装输入法引擎

你至少需要一个支持你所想用的语言的输入法。可用的输入法包括：

```
    ibus-anthy: 一个日文输入法引擎，基于anthy。
    ibus-pinyin: 一个智能中文语音输入法引擎，支持汉语拼音与注音符号。设计者为Ibus的主要作者，而且有许多的高级功能（如英文拼错修改）。 该软件暂时没有维护，而且最新的 ibus 引擎上部分功能不能使用。作为替代，请使用ibus-libpinyin。
    ibus-rime:一个强大的智能中文输入法,支持拼音、注音或者没有音调的拼音、双拼、粤拼、中州韵、仓颉和五笔86。
    ibus-chewing:一个智能中文语音输入法引擎，支持注音符号，基于libchewing。
    ibus-hangul: 一个韩文输入法，基于libhangul。
    ibus-unikey: 支持越南文字的输入法引擎。
    ibus-table: 一个支持查表型输入法的输入法引擎。
    ibus-m17n: 一个m17n输入法引擎，可以用m17n-db数据库中的输入法来输入许多语言。
    ibus-mozc - 个日文输入法引擎, 基于 Mozc. 包含在 mozcAUR 包中。
    ibus-keymagic:一个复合型智能输入法，它被设计成可以工作于所有语言，但需要和kms脚本生成的km2键盘布局共同使用。
```

### 查看所有可用的输入法： 
```bash
$ pacman -Ss ^ibus-*
```

### 安装小狼毫输入法
```bash
$ pacman -S ibus-rime
```

### 初始安装
现在运行ibus-setup的初始程序(需要用Ibus的用户):
```bash
$ ibus-setup
```

它会启动后台程序，并给你这条信息： 

```
IBus has been started! If you cannot use IBus, please add below lines in $HOME/.bashrc, and relogin your desktop.
（译：IBus已启动！如果您还不能用Ibus,请您先将以下的三行代码加到$HOME/.bashrc，再重新登录。)
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
```

**注意:** 虽然Ibus使用一个后台程序，但是它不是被systemd管理的那种后台程序：普通用户也可以运行，当你登录时，它会启动。
 
**注意:** 但是，如果ibus尚未启动，先将那些"export"的代码复制到**$HOME/.xprofile**(这个文件里)，并将这行代码加到该文件后面：**ibus-daemon -x -d**,再**重新登录**。

之后，你会看到一张设置屏幕。Ibus运行时，可以随时访问该屏幕，在系统托盘中的Ibus图符点击右键，选择"Preferences"（选项）即可.

如果Ibus在Qt、KDE应用程序中不工作，保证ibus-qt软件库已安装，并在Qt设置编辑器中将Ibus制定为默认输入法引擎： 

```bash
$ qtconfig-qt4

```

**在 "Interface" -> "Default Input Method" （译：“界面”->“默认输入法引擎”） 中,选择“ibus”,而不是"xim"。 **

### GNOME

GNOME现在已经默认集成了IBus， 所以你只需要安装的输入法引擎并在**Region & Language** 添加输入源。默认切换输入法的快捷键是 **Super+space**; 你可以在终端输入 

```bash
$ ibus-setup
```

进入设置页面来修改。 

