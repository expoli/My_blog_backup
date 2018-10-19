---
layout: post
title:  如何在 Windows 安装 docker
date: 2018-10-17 14:41:08
comments: true
tags:
    - Windows
    - docker
categories:
    - 笔记
---

![](https://ws4.sinaimg.cn/large/006tNbRwly1fwb6v06z2jj30kk0ae0xj.jpg)

## 注意⚠️  因 docker 需要 Hyper-V 虚拟化支持、win10 家庭版无法安装
<!-- more -->

## docker 介绍
[Docker 官网](https://www.docker.com/)

## 安装前准备

* ### 下载 docker windows 安装包
    * [官方网站](https://store.docker.com/editions/community/docker-ce-desktop-windows)
    * [备份](https://pan.shuangzu.top/index.php?share/file&user=102&sid=uS3FTgrE)
    	*   提取密码: `HJmmc`

    * 若官网下载速度缓慢、可考虑使用我的备份

## 开始安装
### 第一步
* 首先安装 docker
    * 和一般 windows 软件的安装没有什么不同
    * 运行下载的 `.exe `安装文件
    * 安装选项选择全部、docker 会自己安装需要的运行环境
    * 根据自己的需要进行安装选项的设置
    * 如果你不清楚具体选项的意义、你完全可以使用默认值、一路下一步就可
### 第二步
* ### 配置优化
* ### 更换软件源
    * 因为某些原因，国内网络环境不是很友好，docker 官方镜像源连接性很差，速度很慢，所以我们需要更换 `daocker` 软件源为国内源

* 推荐国内 `Daoclud` 提供免费的镜像加速服务
    * 首先进入官网 [https://www.daocloud.io/mirror](https://www.daocloud.io/mirror)
    * 注册一个账号 `->` 完善信息 `->` 完成登录操作 `->`进入控制台首页
    * 点击加速器
* ![](https://ws3.sinaimg.cn/large/006tNbRwly1fwb5ci3h45j30nb0cd75h.jpg)
    * 找到相应操作系统平台的加速器配置
* ![](https://ws2.sinaimg.cn/large/006tNbRwly1fwb5v997rwj30v50i7jtx.jpg)s
    * **在** `win10` **托盘里右键** **docker** 
* ![](https://ws2.sinaimg.cn/large/006tNbRwly1fwb519j9zjj30c50b9q3j.jpg)
    * **点击settings**
* ![](https://ws4.sinaimg.cn/large/006tNbRwly1fwb4wqi856j30dz0fwmys.jpg)
    * **按下图将链接粘贴到** `Registry mirrors` **里面**
* ![](https://ws3.sinaimg.cn/large/006tNbRwly1fwb4voklrxj31ae0vxn24.jpg)
    * **点击** `apply` **等待** **docker** **重启完成**
* ### 尽情享用吧！
* ![](https://ws2.sinaimg.cn/large/006tNbRwly1fwb4uqmrh6j30ng0gon01.jpg)


## Docker Toolbox 的使用
* ### 安装 `DockerToolbox` 工具、该工具提供 docker 镜像的可视化管理、适合初学者使用
* ### 下载 `DockerToolbox` 安装包
    * [官网下载地址](https://docs.docker.com/toolbox/toolbox_install_windows/)
    * [备份](https://pan.shuangzu.top/index.php?share/file&user=102&sid=CxkpSsN5)
        * 提取密码: `UIkgi`
    * 若官网下载速度缓慢、可考虑使用我的备份

[Docker Toolbox 官方文档](https://docs.docker.com/toolbox/toolbox_install_windows/#what-you-get-and-how-it-works)

### Docker Toolbox包括以下Docker工具： 

* Docker CLI client for running Docker Engine to create images and containers
* Docker Machine so you can run Docker Engine commands from Windows terminals
* Docker Compose for running the docker-compose command
Kitematic, the Docker GUI
* the Docker QuickStart shell preconfigured for a Docker command-line environment
* Oracle VM VirtualBox

### 开始安装
* 第一步
    * 双击打开下载好的安装包
* ![](https://ws1.sinaimg.cn/large/006tNbRwly1fwb68hjosxj30e80b2q46.jpg)
    * 这是相关的协议介绍、接受 `->` 下一步
    * 接受默认安装选项 `->` 下一步
    * 耐心等待完成。。。直到出现这个界面
* ![](https://ws1.sinaimg.cn/large/006tNbRwly1fwb6c9iuz9j30e90b2my5.jpg)

    * 这时你会发现你电脑桌面上多了3个图标
* ![](https://ws4.sinaimg.cn/large/006tNbRwly1fwb6dyqezxj30bn05pdg0.jpg)
    * 点击 `Kitmatic`
* ![](https://ws3.sinaimg.cn/large/006tNbRwly1fwb6fy6mc6j30nw0eytbw.jpg)
    * 你能在这里看到好多别人打包好的运行环境的镜像、用来做学习使用的开发环境还是很不错的
* ### 选一个你喜欢的、然后愉快地享受便利吧！