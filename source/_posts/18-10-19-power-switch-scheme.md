---
layout: post
title: 一个成熟好用的电池供电切换电路
date: 2018-10-19 13:12:08
comments: true
tags:
    - 硬件
    - 转载
categories:
    - 笔记
---

<center>![switch](https://ws2.sinaimg.cn/large/006tNbRwly1fwdgl3twzij30bh07zdfx.jpg)</center>

### 转自：芯片之家公众号  2016-11-20
* （关注我，你的眼睛会怀孕）

<!-- more -->

## 特点：
* 1、支持轻触开关、自锁开关
* 2、支持外接电源自动上电（焊接上D17即可实现）
* 3、支持待机常电输出
* 4、外接电源、锂电供电自动切换，由于PMOS内续流二极管的存在，切换过程不会出现电压跌落情况。
* 5、通过双PMOS背靠背连接，防止外接电源倒灌至锂电池

## 电源标号说明：
* 1、VCC_5V0  外接电源输入
* 2、LI_BAT     锂电池
* 3、VCC_SYS  主电源输出
* 4、VCC_SB    待机电源输出

## 控制接口说明：
* 1、EX_PWR_KEY     开关按键输入，外接轻触开关或自锁开关，低电平有效。
* 2、PWR_KEY_DET   开关按键检测，给单片机检测开关状态用，主要适用于采用轻触开关。
* 3、SYS_PWR_HOLD 电源保持，高电平有效，当采用轻触开关，或者系统想自己控制关机时有用

## 典型应用：
* 1、电源开关使用轻触开关，通过检测PWR_KEY_DET状态，控制SYS_PWR_HOLD，实现长按xx秒，系统开机，长按xx秒，系统关机。
* 2、车载设备，D17外接ACC信号，实现汽车点火，设备自动开机，汽车熄火，延时xx时间后，自动关机。
* 3、使用自锁开关，断开D17，不用PWR_KEY_DET 与 SYS_PWR_HOLD ，实现外接电源与内置电源自动切换，及小自锁开关控制大电流通断。

### 原理图：
<center> ![](https://ws2.sinaimg.cn/large/006tNbRwly1fwdggqqesuj30m80a8gn9.jpg) </center>


<center> 明天更精彩哦！ </center>

<center> ![芯片之家](https://ws4.sinaimg.cn/large/006tNbRwly1fwdg9paywwj3076076t9c.jpg) </center>

<center> 长按识别二维码
关注“芯片之家公众号” </center>


---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---