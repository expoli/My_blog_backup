---
layout: post
title: nginx 设置反向代理
date: 2018-05-02 21:40:46
comments: true
tags:
	- Nginx
categories:
	- 笔记
---

![Nginx server](https://s1.ax1x.com/2018/10/12/iNA09e.png)

### 反向代理
今天给大家介绍一下 如何 使用nginx 内置的 **反向代理** 功能

<!-- more -->

想使用反向代理功能 只需要在nginx 的 **http 模块** 加入类似于下面的代码就行

```bash
server {
  		listen  port; #你想要监听的端口
	location / {
			proxy_pass  http://1.1.1.1:80; #你想用这个端口代理的网址
		}
	}	
```


