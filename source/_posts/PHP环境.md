---
title: PHP环境
date: 2022-12-23 17:56:46
tags: 记录
categories: 记录
photos: /img/php.jpg
---
## 0. 前言

ε=(´ο｀*)))唉，为了以后不掉坑，现在做个笔记。

## 1. PHP安装

### 1. 下载 PHP

我的下载：VS16 x64 Non Thread Safe (2022-Dec-06 15:55:22)

官方下载地址：[https://windows.php.n...](https://windows.php.net/download/)

### 2. 修改文件

进入目录，拷贝php.ini-production一份命名为php.ini作为php配置文件

### 3. 配置php.in

#### 设置扩展文件路径，找到extension_dir，去掉前面分号并配置扩展库目录，如：
```
extension_dir = "E:\php\env\php-8.0.3\ext"
```
#### 根据需求打开gd、mysqli、pdo_mysql、mbstring、curl等常用扩展使用，去掉前面分号即可，如：extension=gd2
#### 设置时区为中国地区，date.timezone =PRC
#### 设置支持短标签写法，short_open_tag = Off改为short_open_tag = On
#### 开启cgi，以支持nginx与php通信（apache则采用模块化与php通信），分别找到以下关键词进行配置（去掉前面分号;开启）如下：
```
cgi.force_redirect = 1
cgi.fix_pathinfo=1
cgi.rfc2616_headers = 0
```
#### 配置session存储目录，为了安全尽可能设置为外网访问不到的服务器目录
```
session.save_path = "C:/WINDOWS/Temp"
```

然后把这整个文件夹添加到系统变量即可
PHP -v 可查看版本号

说明：执行php命令若报错：PHP Warning: 'C:\Windows\SYSTEM32\VCRUNTIME140.dll' 14.14 is not compatible......需要Visual Studio 2015、2017 和 2019支持，根据实际情况下载安装。

