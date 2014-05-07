---
layout: post
title:  "彻底解决 Eclipse + Android 自动补全卡死的问题（转载）"
date:   2011-05-05 12:26:38
categories: [Android]
tags: [Android, eclipse]
---

原文地址：

[http://blog.csdn.net/delicioustian/archive/2011/03/05/6224938.aspx](http://blog.csdn.net/delicioustian/archive/2011/03/05/6224938.aspx)问题描述：使用Eclipse开发Android应用程序时，一旦碰到代码补全，Eclipse即进入假死状态，CPU满载(单核100%,双核50%,四核25%)...一般十几秒，甚至几十秒才能有相应，严重影响开发心情。Eclipse版本： Helios SR1ADT插件版本： 10解决方法：Android 2.2 Froyo 下载

[http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=froyo;sf=tgz](http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=froyo;sf=tgz)(base-froyo-a45d693.tar.gz)解压缩到Android-SDK\platforms\android-8\sources\重启Eclipse即可实现非常迅速的代码补齐。Android 2.3 GingerBread

下载

[http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=gingerbread;sf=tgz](http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=gingerbread;sf=tgz)(base-gingerbread-4ddd990.tar.gz)解压缩到Android-SDK\platforms\android-9\sources\重启Eclipse即可实现非常迅速的代码补齐。 

[http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=YOURVERSION;sf=tgz](http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=gingerbread;sf=tgz)YOURVERSION = froyo , gingerbread .....参考：[http://code.google.com/p/android/issues/detail?id=7850&q=adt&colspec=ID%20Type%20Status%20Owner%20Summary%20Stars#c7](http://code.google.com/p/android/issues/detail?id=7850&q=adt&colspec=ID%20Type%20Status%20Owner%20Summary%20Stars#c7)This issue is happen because the ADT classpath container have an invalid source attachment by default. It is fixed in https://review.source.android.com/16569. This change enables changing the ADT clasppath container's source attachment and disables setting invalid source attachment. Hoping it will be available in ADT 8.0.0.Namely, ADT classpath container in 0.9.x has the source attachment set to the <SDK_HOME>\platforms\android-<API_LEVEL>\sources directory. This directory doesn't exist in standard SDK. Eclipse try to cache entries in this directory on every access and it slow up auto completion.

Workaround for ADT 0.9.x: attach the valid source attachment as described on 

[http://android.opensourceror.org/2010/01/18/android-source/](http://android.opensourceror.org/2010/01/18/android-source/)