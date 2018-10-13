---
layout: post
title: Ubuntu修改ssh端口
date: 2018-04-27 09:29:59
comments: true
tags:
    - Ubuntu
    - ssh
categories:
    - 笔记
---

![SSH](https://s1.ax1x.com/2018/10/12/iNFevn.png)

首先安装 **openssh-server**

```bash
$ sudo apt-get install openssh-server
```

修改
``` bash
/etc/ssh/sshd_config
```

在Port 22下添加你的端口
``` bash
$ sudo vim /etc/ssh/sshd_config
```

修改
``` bash
/etc/ssh/ssh_config
```

``` bash
$ sudo vim /etc/ssh/ssh_config
```

把 # port 22前面的 # 去掉，并在下一行添加 你想要使用的端口 eg: Port ****

### 修改保存后 重启服务

``` bash
$ /etc/init.d/ssh restart     
```
or
``` bash
$ service ssh restart 
```

然后在防火墙开启相应端口，进行测试 （注意现在ssh同时工作在22和你设定的端口下，测试完毕后你可以选择把22端口注释掉。

### OK！ 大功告成！

