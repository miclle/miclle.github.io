---
layout: post
title:  "申请 Google Map apiKey"
date:   2011-05-13 18:41:55
categories: [Android]
tags: [Android, Google, Map, apikey]
---

1. 找到debug keystore所在位置：

Eclipse--->偏好设置--->Preferences--->Android--->Build

如：2. 

在命令行下输入：keytool -list -alias 

androiddebugkey -

keystore 

 -

storepass 

android -

keypass 

android

其中：

  -list：在终端打印出证书的MD5指纹

  -

keystore 

<keystore-name>.

keystore：目标密钥所在的密钥库

  -

storepass 

<password>：密钥库密码

  -alias 

<alias_name>：密钥库内生成MD5指纹的密钥别名

  -

keypass 

<password>：指定密钥密码结果：  androiddebugkey, 2010-12-8, PrivateKeyEntry,认证指纹 (MD5) 17:DA:87:2B:7D:DE:63:9A:13:51:5A:9B:69:87:F8:EE

3、有了MD5密码就可以到

Google Map API密钥的生成页面：

http://code.google.com/intl/zh-CN/android/maps-api-signup.html 申请Map API密钥了：4.感谢您注册 Android 地图 API 密钥！

您的密钥是：

0Q_rEYqQ22lJwXu_IBOIP9AfTXB4GbveC1qtpXQ

此密钥适用于所有使用以下指纹所对应证书进行验证的应用程序：

17:DA:87:2B:7D:DE:63:9A:13:51:5A:9B:69:87:F8:EE

下面是一个 xml 格式的示例，帮助您了解地图功能：

<com.google.android.maps.MapView

android:layout_width="fill_parent"

android:layout_height="fill_parent"

android:apiKey="0Q_rEYqQ22lJwXu_IBOIP9AfTXB4GbveC1qtpXQ"/>