---
layout: post
title: 使用 ADB 进行文件的传输操作
date: 2018-10-12 18:41:08
comments: true
tags:
    - ADB
categories:
    - 笔记
---

![ADB](https://ws1.sinaimg.cn/large/006tNbRwly1fwblcmi4crj30zk0gotao.jpg)

## 使用 ADB 进行文件的传输操作

### ADB 的安装

<!-- more -->

* ADB 官网下载链接
[SDK Platform Tools release notes | Android Developers](https://developer.android.com/studio/releases/platform-tools)

### Windows 平台
[下载 ANDROID SDK PLATFORM-TOOLS FOR WINDOWS](https://dl.google.com/android/repository/platform-tools-latest-windows.zip)

* ### 安装步骤    
    * 下载 ADB
    * 解压
    * 把系统 `C:\Windows\System32` 目录里的 `cmd.exe` 程序复制出来，与adb工具放在同一目录，要用adb工具时直接双击cmd.exe就可以了
    * 输入 `adb version`，查看adb版本，验证adb是否可用

* ### 使用
    * 将手机使用usb连接到电脑
        * 打开手机的开发者模式
        * 打开开发者模式中的 `USB调试`
        * 在cmd里面输入 `adb devices` 
        * 如果出现手机未识别的提示，则在手机上同意 `USB调试的权限授权`
        * 再次输入 `adb devices`
        * `offline —— 表示设备未连接成功或无响应。device —— 设备已连接。no device —— 没有设备/模拟器连接。`

    * 使用无线将手机连接电脑
        * `adb tcpip 5555`
        * `adb connect ipAddress`
        * 使用`adb devices`查看设备是否连接上
        * 断开无线 `adb disconnect ipAddress`
    * 启动/停止 `adb  server`
        * adb start-server/adb kill-server
        
    * 使用 ADB 传输文件
        * 从手机向电脑传输文件：
            * 输入: 
            `adb pull 手机存储路径  电脑路径`
            `adb pull  /sdcard/xxx  /Users/xxxx/xxx`
        * 从电脑向手机传输文件：
            * 输入：
            `adb push 电脑路径  手机存储路径  `
            `adb push  /Users/xxxx/xxx   /sdcard/xxx`


### MacOS 平台
* ### 手动安装 [下载 ANDROID SDK PLATFORM-TOOLS FOR MAC](https://dl.google.com/android/repository/platform-tools-latest-darwin.zip)

    * 如果你以前安装过、请删除老文件
        * `rm -rf ~/.android-sdk-macosx/`
    * 将下载的文件解压到 ~/.android-sdk-macosx

    * 运行 SDK Manager
        * `sh ~/.android-sdk-macosx/tools/android`
    * 根据你的需要选择，（我只需要Android SDK Platform-tools）［可选步骤］

    * 选好后 Install

    * 环境变量设置
        * `echo 'export PATH=$PATH:~/.android-sdk-macosx/platform-tools/' >> ~/.bash_profile`

    * 更新配置文件
        * `source ~/.bash_profile`

    * 测试是否正常安装
        * `adb devices`

* ### 通过 **Homebrew** 安装
    * `brew cask install android-platform-tools`

* ### 测试
    * `adb devices`
    

### Linux 平台
* ### 手动安装 [下载 ANDROID SDK PLATFORM-TOOLS FOR LINUX](https://dl.google.com/android/repository/platform-tools-latest-linux.zip)

* ### 命令操作
    * debine系列的系统可以使用 `sudo apt-get install android-tools-adb`
    * 如果发现源中没有这个程序：

    ```bash
    sudo add-apt-repository ppa:nilarimogard/webupd8
    sudo apt-get update
    sudo apt-get install android-tools-adb
    ```

