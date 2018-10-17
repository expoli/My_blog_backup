---
layout: post
title: 解决Windows与Linux双系统时间同步问题
date: 2018-05-02 11:30:29
comments: true
tags:
    - Linux
    - Windows
    - 时间同步
categories:
    - 笔记
---

![time](https://ws4.sinaimg.cn/large/006tNbRwly1fwbme1ai1oj30sg0g0tbp.jpg)

### 问题发现

本子上装的是Window 10和 manjaro 的双系统, 一直以来都发现双系统切换后系统的时间显示有问题\每次都发现进入ubuntu系统的时间显示不正确, 只有再重新使用网络对时之后系统的时间才正常.

<!-- more -->

但是问题不仅于此, 切环回window之后, 会发现系统的时间也不正常了, window一直是网络自动对时的啊, 然后无语, 只能再次打开联网强制同步网络时间.

如此以来好几个星期了老是没顾得上解决, 今天难得想起来, 就花时间整了整.

### 问题原因

Linux和Windows默认的时间管理方式不同，所以双系统发生时间错乱是正常的

Linux默认时间是把BIOS时间当成GMT+0时间，也就是世界标准时，而我国在东八区（GMT+8），所以如果你的Linux位置是中国的话你系统显示的时间就是BIOS时间+8小时, 假如现在是早上8点，那么你Linux会显示8点

而当你切换到Windows系统时就会发生时间错乱，因为Windows会认为BIOS时间就是你的本地时间，结果就是Windows显示时间为0点……而假如你在Windows下同步时间，恢复显示为8点，这时BIOS时间也会被Windows改写成8点，再次进入Linux时显示时间又变成了8+8=16点。

### **WINDOWS的时间和时区**

Windows操作系统直接把CMOS时间认定为当前显示时间，不根据时区转换。这样每调整一次系统时区，系统会根据调整的时区来计算当前时间，确定后，也就同时修改了CMOS内的时间（即每调整一次时区，设置保存后，CMOS时间也将被操作系统改变一次，注意不同操作系统调整时间后，也会同时改变CMOS时间，这一点是共通的）。


### **LINUX的时间和时区**

Linux和苹果操作系统以当前主板CMOS内时间做为格林威治标准时间，再根据系统设置的时区来最终确定当前系统时间（如时区设置为GMT+08:00北京时间时以及当前CMOS时间为03:00，那么系统会将两个时间相加得出显示在桌面的当前系统时间为11:00）

### 问题解决

    在Windows使用Ubuntu的时间管理方式，就是启用UTC（世界协调时）

### 在Windows下启用UTC

打开运行窗口（快捷键Win+R），然后输入 **regedit** 启动注册表编辑器，并找到一下目录位置：
```bash
HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Control/TimeZoneInformation/
```

添加一项类型为REG_DWORD的键值，命名为RealTimeIsUniversal，值为1然后重启后时间即回复正常

