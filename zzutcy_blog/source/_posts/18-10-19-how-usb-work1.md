---
layout: post
title: 你真的了解USB吗？USB充电大揭秘(二)
date: 2018-10-19 13:04:08
comments: true
tags:
    - 硬件
    - 转载
categories:
    - 笔记
---

![usb](https://ws3.sinaimg.cn/large/006tNbRwly1fwdft5gx50j30m80ciwfc.jpg)

### 转自：芯片之家公众号  2016-12-22 原创： karaxiaoyu
* （关注我，你的眼睛会怀孕）

<!-- more -->

## 前言

### 上回我们说到了BC1.2引入的几个P玩意，今天我们来看一下CDP和DCP是怎么一个实现方式。
* 我们先从DCP说起，因为它最简单。可能很多人都知道，所谓DCP，听起来很高大上，实际上淘宝上无数山寨的充电器早就搞定了：
    * 就是用一个200欧姆的电阻短接D+和D-就可以了（更有甚者，连这200欧姆的电阻都省了。。。），对，你没看错，就是这么简单！
    * 但是，实际上DCP的协商过程还是要比这个短接电路稍微复杂一点点。

<center> ![](https://ws1.sinaimg.cn/large/006tNbRwly1fwdg8l0zolj30fe0g4q45.jpg) </center>

 * DCP端口，RDCP_DAT就是这个200欧姆的电阻
 * 首先手机会在D+上产生一个0.6V的电压，然后测量D-上的电压。如果主机USB是一个传统的USB端口，不支持BC1.2，那么在D-上会有一个15K的下拉电阻（前文有提过），D-上的电压就为0，因此手机只能以500mA的电流进行充电。反之，如果手机在D-上测量到一个0.6V的电压，那么双方即握手成功。这就是DCP的协商过程。这个过程其实很好理解，因为D+和D-在DCP模式下，是通过200欧姆电阻短接的，当然手机在D+上产生的0.6V，会直接在D-上也得到一个0.6V的电压，这样自然而然的，协商就成功了。但我估计这会各位童鞋已经忘了啥是DCP，啥是CDP了，下面我再无私奉献一遍：

```
在BC1.2的标准里面，定义了3种USB的端口，分别是：

SDP——Standard Downstream Port，标准下行口

CDP——Charging Downstream Port，充电下行口

DCP——Dedicated Charging Port，专用充电口
```

### 作为对比，可以看一下SDP端口，可以看出在D+和D-上各有1个15K的下拉电阻：

<center> ![](https://ws2.sinaimg.cn/large/006tNbRwly1fwdg8w3gldj30fe0ev0tt.jpg) </center>

* SDP端口，2个15K的下拉电阻

* 这只是协商过程的第一步，这一步的意义在于，把SDP排除掉。因为如果这一步失败了，就表明USB主机和USB设备至少有一个不支持BC1.2充电协议，那么大家就乖乖的按照传统的500mA充电就是了。如果这一步成功了，就表明双方至少已经支持BC1.2了，至于到底是支持DCP还是CDP，就要靠第二步握手来区别了。

* 在第二步的协商机制里面，手机首先在D-上产生一个0.6V的电压，然后测量D+上的电压（跟第一步正好反过来）。我们已经知道DCP模式下，D+和D-是通过200欧姆电阻短接的，当然手机在D-上产生的0.6V，会直接在D+上也得到一个0.6V的电压。所以如果D+的电压测出来是0.6V，那么手机就知道自己插入了一个DCP端口，只管放心充电，数据就不管了。反之，如果手机在D+上测到一个0电压，它就知道自己插入了一个CDP端口，紧接着USB主机会开始枚举，正常的数据通信就开始了。

### 下图是一个CDP的握手过程波形，可以清楚的看到，
* 第一步，手机在D+上产生了0.6V（1），然后在D-上也出现了0.6V（2）；
* 第二步，手机在D-上产生了0.6V（3），但是在D+上却是0V，因此，CDP握手成功了，后面就开始了D+/D-上的数据通信，枚举开始了。

<center> ![](https://ws2.sinaimg.cn/large/006tNbRwly1fwdg94hqe7j30fe09wdgk.jpg) </center>

<center>  CDP握手过程示意 </center>

<center> ![](https://ws2.sinaimg.cn/large/006tNbRwly1fwdg9ga665j30fe0ezjso.jpg) </center>

<center> CDP端口，要复杂一些 </center>

BC1.2到这里基本上就介绍完了，可是对于USB充电来说，这才刚刚上路。BC1.2里面规定了USB设备（主要是手机，平板电脑）最大不得以超过1.5A的电流进行充电，这个电流对于手机来说，勉强可以接受，但是对于平板和某些大容量电池的note手机来说，仍然显得比较慢。大家熟知的苹果12W充电器，可以提供5V，2.4A的充电电流，显然，如果iPad以BC1.2的充电标准来充电，还是慢了一些。但是这还不够快，大家近来经常看到诸如“充电5分钟，通话2小时”之类的广告所宣传的快充，还有QC2.0，3.0的快充等等，这些东西又是怎么回事呢？USB-IF组织有没有出台新的统一的快速充电标准呢？我们下回接着说，我先歇几天！

[原文链接](https://mp.weixin.qq.com/s/tardc2DavW5gdOolHbmh6A?)

<center> 明天更精彩哦！ </center>

<center> ![芯片之家](https://ws4.sinaimg.cn/large/006tNbRwly1fwdg9paywwj3076076t9c.jpg) </center>

<center> 长按识别二维码
关注“芯片之家公众号” </center>


---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---