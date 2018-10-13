---
title: nginx 设置目录访问权限
date: 2018-04-16 23:42:46
cover: https://s1.ax1x.com/2018/10/12/iNAdhD.png
tags:
- nginx
categories:
- 笔记
---
### 一、创建htpasswd文件

可以使用下面这个python脚本生成认证文件
`bash
https://gist.githubusercontent.com/kelvinblood/efd9d19cc981f71b3f94ee0e04f2ea96/raw/b84137bc2024d30d4ab57a778b5938e9eeef0632/htpasswd.py
`

### 二、执行命令 授予执行权限

``` bash
chmod 777 htpasswd.py ./htpasswd.py -c -b filename username password
```

其中htpasswd是生成的文件名，username 是用户名，password 是对应的密码

### 然后把生成的文件复制到你nginx的文件夹里面 eg:/etc/nginx/

修改nginx的conf 或nginx的虚拟服务器配置文件的server 条目 加上这两句

```
# 设置访问权限
auth_basic "Restricted";#访问权限类型
auth_basic_user_file /etc/nginx/htpasswd;#用户名单
```

然后重启nginx

``` bash
$ sudo nginx -s relaod
```

### OK！
