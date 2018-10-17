---
layout: post
title: 给本子安装manjaro 出现无法关机的解决办法
date: 2018-04-29 09:59:04
comments: true
tags:
    - Manjaro
    - 坑
categories:
    - 笔记
---

![Manjaro shut down](https://ws3.sinaimg.cn/large/006tNbRwly1fwbm1hqghmj311y0lcgnd.jpg)

**manjaro-kde-17.1.8-stable** 和** win10** 双系统 总是发现在关机或者重启的时候，无法关掉电源，只能按电脑的电源按钮才可以强行关掉， 最后通过以下办法才解决。

<!-- more -->

### 方案一

* 首先编辑**/etc/default/grub**文件，再该文件下查找**GRUB_CMDLINE_LINUX=""**一行，修改为：
```bash
GRUB_CMDLINE_LINUX="reboot=efi"
```

* 然后执行如下命令：
```bash
$ sudo update-grub
```
* 更新**/boot/grub/grub.cfg**文件。

    * 注：更新完了之后，默认grub菜单的选择时间为10秒，可以按照自己的需求修改。

    * 注：如果上边修改的/etc/default/grub文件，没有作用，可以继续尝试替换为下边的几种内容。

```
GRUB_CMDLINE_LINUX="reboot=bios"

GRUB_CMDLINE_LINUX="reboot=acpi"

GRUB_CMDLINE_LINUX="reboot=pci"
```

### 方案二
在终端用打开编辑 **/boot/grub/grub.cfg** 文件：

```bash
#sudo vi  /boot/grub/grub.cfg
```
找到下面内容（在第**140**行附近）：

 
```
inux --class gnu --class os {

        recordfail

        gfxmode $linux_gfx_mode

        insmod gzio

        insmod part_msdos

        insmod ext2

        set root='(hd0,msdos11)'

        search --no-floppy --fs-uuid --set=root ed532c1f-b89a-470c-ad6f-539a3f04b993

        linux   /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=ed532c1f-b89a-470c-ad6f-539a3f04b993 ro   quiet splash $vt_handoff **acpi=force**

        initrd  /boot/initrd.img-3.2.0-24-generic-pae

}
```

如上面 **acpi=force** 标记，在此处加上**acpi=force** **保存退出**。

### 方案三 

**有可能是显卡驱动的问题**
可尝试 屏蔽开源驱动**nouveau**

```bash
$ sudo vim /etc/modprobe.d/blacklist.conf
```
然后添加如下内容：
```
blacklist vga16fb

blacklist nouveau

blacklist rivafb

blacklist nvidiafb

blacklist rivatv
```
**重启测试**

## 方案四

```bash
1.安装 watchdog
sudo apt install watchdog

2.开启 watchdog 服务
sudo systemctl enable watchdog.service

3.马上启用 watchdog 服务
sudo systemctl start watchdog.service
```

**我 Asus FX50V 主板 采用的是 方案一 的ACPI 和 方案 二 进行解决的**

**希望能够帮到你!**
