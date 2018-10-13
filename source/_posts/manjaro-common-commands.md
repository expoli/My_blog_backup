---
layout: post
title: manjaro pacman 命令介绍
date: 2018-05-01 09:24:03
comments: true
tags:
    - Manjaro
    - pacman
categories:
    - 笔记
---

![Pacman](https://s1.ax1x.com/2018/10/12/iNkjOI.png)

manjaro 这款发行版所使用的包管理器Arch linux  的 **pacman软件包管理器** 

pacman软件包管理器是 Arch Linux 的一大亮点。它将一个简单的二进制包格式和易用的构建系统结合了起来(参见makepkg和ABS)。不管软件包是来自官方的 Arch 库还是用户自己创建，pacman 都能方便地管理。 

pacman 用 C 语言编写，使用tar打包格式。
提示： pacman 软件包还提供了其它有用工具，例如 makepkg、pactree、vercomp、 checkupdates等。可以通过 pacman -Ql pacman | grep bin 获取工具列表。

pacman 命令有很多在这里我列出来 几条常用的命令

### 升级软件包

```bash
# pacman -Syu
```

### 安装指定的包

安装或者升级单个软件包，或者一列软件包（包含依赖包），使用如下命令：
```bash
# pacman -S package_name1 package_name2 ...
```

### 安装包组

一些包属于一个可以同时安装的**软件包组**。例如，运行下面的命令
```bash
# pacman -S gnome
```
会提醒用户选择 gnome 内需要安装的包。

有的包组包含大量的软件包，有时用户只需其中几个。除了逐一键入序号外，pacman 还支持选择或排除某个区间内的的软件包：

```bash
Enter a selection (default=all): 1-10 15
```

这将选中序号 1 至 10 和 15 的软件包。而

```bash
Enter a selection (default=all): ^5-8 ^2
```

将会选中除了序号 5 至 8 和 2 之外的所有软件包。

想要查看哪些包属于 gnome 组，运行：

```bash
# pacman -Sg gnome
```

也可以访问 https://www.archlinux.org/groups/ 查看可用的包组。 

### 删除软件包

删除单个软件包，保留其全部已经安装的依赖关系
```bash
# pacman -R package_name
```

删除指定软件包，及其所有没有被其他已安装软件包使用的依赖关系：
```bash
# pacman -Rs package_name
```

要删除软件包和所有依赖这个软件包的程序:
**警告: 此操作是递归的，请小心检查，可能会一次删除大量的软件包。**
```bash
# pacman -Rsc package_name
```

要删除软件包，但是不删除依赖这个软件包的其他程序：
```bash
# pacman -Rdd package_name
```

pacman 删除某些程序时会备份重要配置文件，在其后面加上*.pacsave扩展名。-n 选项可以避免备份这些文件：
```bash
pacman -Rn package_name
```
**注意: pacman 不会删除软件自己创建的文件(例如主目录中的 .dot 文件不会被删除。**

### 清理软件包缓存

pacman 将下载的软件包保存在 **/var/cache/pacman/pkg/** 并且不会自动移除旧的和未安装版本的软件包，因此需要手动清理，以免该文件夹过于庞大。

使用内建选项即可清除未安装软件包的缓存：
```bash
# pacman -Sc
```

**警告:仅在确定当前安装的软件包足够稳定且不需要降级时才执行清理。pacman -Sc仅会保留软件包的当前有效版本，旧版本的软件包被清理后，只能从其他地方如 Arch Linux Archive (简体中文)中获取了。**
**pacman -Scc 可以清理所有缓存，但这样 pacman 在重装软件包时就只能重新下载了。除非空间不足，否则不应这么做。**
