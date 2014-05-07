---
layout: post
title:  "Android ADT插件的安装和升级（转载）"
date:   2011-06-13 14:28:59
categories: [Android]
tags: [Android, ADT]
---

安装和升级的步骤：

1.

      通过eclipse

在线安装和升级

方法一：

打开

eclipes，选择

Help->check for update，搜索完后，会显示可以升级的

ADT，选中需要升级的

ADT，点击

Next，再次点击

Next确认，选择同意并点击

Finish，等待更新完毕。（有可能会不成功，但是不知道为什么会失败）

 

方法二：

1).

     打开eclipes

，选择Help->Install New Software…->

选择work with:

后的Add…

2).

     在Name

选项输入

Android Plugin

，在Location

输入

http://dl-ss.google.com/android/eclipse/，点击OK

，然后在下面勾选Name

中的选项即可。（未试过）

 

2.      离线安装和升级

Android ADT-0.9.9.zip

官方下载地址：http://dl.google.com/android/ADT-0.9.9.zip

1).

     打开eclipse

，选择Help->Install New Software…->

选择work with:

后的Add…

2).

     在Local

选项输入Android Plugin

，在Archive

中找到ADT0.9.9

的压缩包，点击OK

，然后在下面勾选Name

中的选项即可。

 

测试安装是否成功：

1).     安装完

ADT插件后，关闭

eclipse，然后重启。

2).     打开

File->New，看有无出现

Android Project选项，若没有，再点击

Other…选项，看看

General选项下是否有

Android选项，有，则安装成功，无，则安装失败。

 

查看已安装的

ADT版本：

打开eclipse

，选择Help->About Eclipse

，点击Installation Details->Installed Software

。原文地址：

[http://www.51testing.com/?uid-115892-action-viewspace-itemid-222884](http://www.51testing.com/?uid-115892-action-viewspace-itemid-222884)