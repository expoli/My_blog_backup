---
layout: post
title: 我的 nginx config 备份
date: 2018-04-16 22:27:30
comments: true
tags:
	- Nginx
categories:
	- 笔记
---

![Nginx](https://ws4.sinaimg.cn/large/006tNbRwly1fwbmakjhg4j314k0ka751.jpg)

### 最近一段时间折腾了一下Nginx 在这里分享一下自己的配置文件 有需要的朋友可以看下

### Nginx服务配置文件：Nginx.conf 

<!-- more -->

``` bash
$ sudo vim /etc/nginx/nginx.conf
```

``` 
user www-data;
pid /var/run/nginx.pid;
worker_processes 4;
worker_rlimit_nofile 100000;

events {
  worker_connections 2048;
  multi_accept on;
  use epoll;
}

http {
  server_tokens off;
  sendfile on;
  tcp_nopush on;
  tcp_nodelay on;
    
  access_log off;
  error_log /var/log/nginx/error.log crit;
    
  keepalive_timeout 10;
  client_header_timeout 10;
  client_body_timeout 10;
  reset_timedout_connection on;
  send_timeout 10;
    
  limit_conn_zone $binary_remote_addr zone=addr:5m;
  limit_conn addr 100;
    
  include /etc/nginx/mime.types;
  default_type text/html;
  
  autoindex on; #列出文件目录
  autoindex_exact_size off; #人性化显示文件大小
  autoindex_localtime on;
 #  autoindex_ignore “header.html” “footer.html”; #屏蔽美化的html显示
  charset utf-8,gbk; #避免中文乱码

# 对页面进行美化
# fancyindex on;
#  fancyindex_ignore “header.html” “footer.html”; #屏蔽美化的html显示
#  fancyindex_exact_size off;
#  fancyindex_header "header.html";
#  fancyindex_footer "footer.html";

  gzip on;
  gzip_disable "msie6";
  gzip_proxied any;
  gzip_min_length 1000;
  gzip_comp_level 6;
  gzip_types text/plain
             text/css
             application/json
             application/x-javascript
             text/xml
             application/xml
             application/xml+rss
             text/javascript;
    
  open_file_cache max=100000 inactive=20s;
  open_file_cache_valid 30s;
  open_file_cache_min_uses 2;
  open_file_cache_errors on;
    
  include /etc/nginx/conf.d/*.conf;
  include /etc/nginx/sites-enabled/*;
}


#mail {
#	# See sample authentication script at:
#	# http://wiki.nginx.org/ImapAuthenticateWithApachePhpScript
# 
#	# auth_http localhost/auth.php;
#	# pop3_capabilities "TOP" "USER";
#	# imap_capabilities "IMAP4rev1" "UIDPLUS";
# 
#	server {
#		listen     localhost:110;
#		protocol   pop3;
#		proxy      on;
#	}
# 
#	server {
#		listen     localhost:143;
#		protocol   imap;
#		proxy      on;
#	}
#}

```

### 虚拟主机配置文件 

``` bash
$ sudo vim /etc/nginx/conf.d/file_server.conf
```

```
server {
    listen  ****; #端口监听
    server_name    ********; # 自己PC的ip或者服务器的域名
    charset utf-8,gbk; # 避免中文乱码
    location / {
	root /home/****/****; # 存放文件的目录
	charset utf-8,gbk; # 避免中文乱码
        autoindex on; # 索引
        autoindex_exact_size off; # 显示文件大小
        autoindex_localtime on; # 显示文件时间
# 页面美化
	fancyindex on;
	fancyindex_ignore “header.html” “footer.html”; #屏蔽美化的html显示
	fancyindex_exact_size off;
	fancyindex_header "header.html";
	fancyindex_footer "footer.html";

# 设置访问权限
	auth_basic "Restricted";#访问权限类型
	auth_basic_user_file /etc/nginx/htpasswd;#用户名单
    }
}

```
