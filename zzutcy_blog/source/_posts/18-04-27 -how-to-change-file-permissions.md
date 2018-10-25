---
layout: post
title: 怎样更改Linux的文件权限
date: 2018-04-27 09:13:41
comments: true
tags:
    - Linux
    - 文件权限
categories:
    - 笔记
---

![Lunux file attributes](https://ws4.sinaimg.cn/large/006tNbRwly1fwbm3gzl0qj30kn05paat.jpg)

### 介绍
好了,当我们已经知道档案权限对于一个系统的安全重要性,也知道档案的权限对于使用者与群组的相关性后, 好了,那么如何修改一个档案的权限呢?又有多少档案的权限我们可以修改呢? 

<!-- more -->

其实一个档案的权限很多嘛!大致上我们先介绍几个简单的,例如:群组、拥有者、各种身份的权限等等。

• chgrp :改变档案所属群组

• chown :改变档案所属人

• chmod :改变档案的属性、 SUID 、等等的特性

### 改变所属群组, chgrp

改变一个档案的群组真是很简 单的,直接以 chgrp 来改变即可,咦!这个指令就是 change group 的缩写
嘛!对啦!这样就很好记了吧! ^_^。不过,请记得, 要改变成为的群组名称必须要在 /etc/group 里面
存在的名称才行,否则就会显示错误！

### 改变档案拥有者, chown

好了,那么如何改变一个档案的 拥有者呢?很简单呀!既然改变群组是 change group ,那么改变拥有者
就是 change owner 啰!BINGO,对啦!那就是 chown 这个指令的用途,要注意的是,使用者必须是已经
存在系统中的,也就是在 /etc/passwd 这个档案中有纪录的使用者名称才行改变。

### 改变九个属性, chmod

档案属性的改变使用的是 ch mod 这个指令,但是,属性的设定方法有两种, 分别可以使用数字或者是符
号来进行属性的变更。

•数字类型改变档案权限
Linux 档案的基本属性就有九 个,分别是 owner/group/others 组别的 read/write/excute 属性。

```bash
-rwxrwxrwx
```

这九个属性是三个三个一组的!其中,我们可以使用数字来代表各个属性,各属性的对照表如下

```bash
r:4
w:2
x:1
```

同一组 (owner/group/others) 的三个属性 (r/w/x) 是需要累加的,例如当属性为 [-rwxrwx---] 则是:

```
owner = rwx = 4+2+1 = 7
group = rwx = 4+2+1 = 7
others= --- = 0+0+0 = 0
```
### chmod 使用方法：
```
                       u                +(加入) r
chmod                  g                -(除去) w                             档案或目录
                       o                =(设定) x
                       a                
```

### 来 实作一下吧!


---
### 文章作者:[糖醋鱼](http://zzutcy.top)

### 版权声明:转载请注明来自[糖醋鱼的博客](http://zzutcy.top)
---