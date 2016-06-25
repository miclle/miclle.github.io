---
layout: post
title:  "Installing Go on the Raspberry Pi"
date:   2014-10-25 1:02:00
categories: [post]
tags: [GO, Raspberry Pi]
---


最近在看《GO语言程序设计》，另一个做嵌入式开发的小伙伴问我 Raspberry Pi 的问题，临时想到能不能在 Raspberry Pi 里搭一个 GO 的环境呢？之前在里面搭过 ruby 的环境，GO 这种静态语言效率应该会更高一点。

## 下载源码
Golang的文档上说是支持多平台的，其中也包括了ARM，下载页面：

```
http://code.google.com/p/go/downloads/list
```

没有找到 ARM 平台的二进制包下载。所以 ARM 平台下的需要下载源码自己编译。

下载源码，两种方式：一种是直接下载压缩包文件(推荐)，另一种是 clone 源代码

```
hg clone -u default https://code.google.com/p/go /home/go
```
我一般会安装在 /usr/local 目录下。


## 安装依赖包
以编译安装前需要安装以下依赖包：`mercurial` `gcc` `libc6-dev`

```
sudo apt-get install -y mercurial gcc libc6-dev
```

## 编译
```
% cd /home/go/src
% ./all.bash
```
这是一个漫长的过程，大概花了近一个小时，安装成功后你会见到这些信息：

```
ALL TESTS PASSED

---
Installed Go for linux/arm in /home/go
Installed commands in /home/go/bin
```

## 配置GO的环境变量
```
export PATH=$PATH:$HOME/go/bin
```
测试：

```
go version
```


