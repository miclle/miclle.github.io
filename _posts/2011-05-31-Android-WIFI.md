---
layout: post
title:  "Android WIFI"
date:   2011-05-31 06:31:02
categories: [Android]
tags: [Android, WiFi, 权限, 网络, 状态]
---

  Android WIFI网卡有一些状态，由一系列的整形常量来表示：

常量名

常量值

网卡状态 WIFI_STATE_DISABLED         

1      

 WIFI网卡不可用 WIFI_STATE_DISABLING               

0

 WIFI正在关闭 WIFI_STATE_ENABLED

3

 WIFI网卡可用 WIFI_STATE_ENABLING

2

 WIFI网卡正在打开 WIFI_STATE_UNKNOWN

4

 未知网卡状态

在应用程序中操作WIFI网卡一定的权限，主要操作权限有四个： 

<!--允许修改网络状态的权限-->

<uses-permission android:name="android.permission.CHANGE_NETWORK_STATE" />  

<!--允许修改 WIFI 状态的权限-->

<uses-permission android:name="android.permission.CHANGE_WIFI_STATE" />  

<!--允许访问网络状态的权限-->

<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />  

<!--允许访问 WIFI 状态的权限-->

<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" /> 

改变WIFI网卡的状态

  对WIFI网卡进行操作需要通过WifiManager对象来进行，获取该对象的方法如下： 

  WifiManager wifiManger=(WifiManger)Context.getSystemService(Service.WIFI-SERVICE); 

  wifiManager.setWifiEnabled(true); //打开WIFI网卡

  wifiManager.setWifiEnabled(false); //关闭WIFI网卡

  wifiManager.getWifiState();//获取网卡当前的状态