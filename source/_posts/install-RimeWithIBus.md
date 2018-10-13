---
title: Ubuntu 安装小狼豪输入法
date: 2018-04-24 20:03:18
cover: https://s1.ax1x.com/2018/10/12/iNkHYD.png
tags:
- Ubuntu
- 小狼毫
categories:
- 笔记
- 工具推荐
---

今天给大家推荐一款广受好评的一款 Linux 中文输入法  **小狼豪**输入法。

小狼豪输入法 开源 可以自己 添加功能，开发词库 等等。。

下面介绍一下 安装方法

### Ubuntu 12.04 and higher

```bash
# this repo provides libkyotocabinet, libgoogle-glog for Ubuntu 12.04;
# these packages are officially supported since Ubuntu 12.10. 

sudo add-apt-repository ppa:fcitx-team/nightly 

# providing libyaml-cpp0.5, librime, rime-data, ibus-rime 
sudo add-apt-repository ppa:lotem/rime

sudo apt-get update
sudo apt-get install ibus-rime
```

### 安裝更多輸入方案：（推薦使用 /plum/ 安裝最新版本）

```bash
# 朙月拼音（預裝） 
sudo apt-get install librime-data-luna-pinyin 
# 雙拼 
sudo apt-get install librime-data-double-pinyin 
# 宮保拼音 
sudo apt-get install librime-data-combo-pinyin 
# 注音、地球拼音 
sudo apt-get install librime-data-terra-pinyin librime-data-bopomofo 
# 倉頡五代（預裝） 
sudo apt-get install librime-data-cangjie5 
# 速成五代 
sudo apt-get install librime-data-quick5 
# 五筆86、袖珍簡化字拼音、五筆畫 
sudo apt-get install librime-data-wubi librime-data-pinyin-simp librime-data-stroke-simp 
# IPA (X-SAMPA) 
sudo apt-get install librime-data-ipa-xsampa 
# 上海吳語 
sudo apt-get install librime-data-wugniu 
# 粵拼 
sudo apt-get install librime-data-jyutping 
# 中古漢語拼音 
sudo apt-get install librime-data-zyenpheng
```

### [官方安装手记](https://github.com/rime/home/wiki/RimeWithIBus)
