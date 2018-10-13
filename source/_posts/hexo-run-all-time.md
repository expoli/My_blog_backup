---
title: 让hexo一直在后台运行
date: 2018-05-02 06:41:31
cover: https://s1.ax1x.com/2018/10/12/iNkoTK.png
tags:
- hexo
categories:
- 笔记
---

## 背景

估计有好多朋友 和我一样，在最初部署成功hexo这个开源博客的时候，很高兴的用**$ hexo server**在服务上跑了起来。

都遇到了 h的exo 进程无法一直常驻后台 ssh 一关，博客进程就死掉了。这可就扎心了，因为我们不可能一直本地开着ssh吧。

于是经过一番大肆搜索，官方说用**$ hexo s &** 但是我在用的时候还是进程莫名奇妙的死掉了

今天给大家介绍一个方法 那就是 用pm2 来接管hexo的进程

### 开始操作

**安装pm2**

```bash
$ npm  install -g pm2
```
### 写一个执行脚本

在博客根目录下面创建一个 **hexo_run.js**

```bash
//run
const { exec } = require('child_process')
exec('hexo server',(error, stdout, stderr) => {
        if(error){
                console.log('exec error: ${error}')
                return
        }
        console.log('stdout: ${stdout}');
        console.log('stderr: ${stderr}');
})
```

### 运行脚本

在根目录下
```bash
pm2 start hexo_run.js
```

**ok! 大功告成！ 尽情的写你的博客吧！**
