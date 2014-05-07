---
layout: post
title:  "Android selector问题"
date:   2011-06-13 06:47:36
categories: [Android]
tags: [Android, selector, setOnClickListener, ontouch]
---

layout代码片断如下：<RelativeLayout

android:layout_width="fill_parent" android:layout_height="wrap_content"

android:background="@drawable/list_item_background">

<ImageView android:src="@drawable/icon_period"

android:layout_width="wrap_content" android:layout_height="wrap_content"

android:layout_centerVertical="true" android:layout_marginLeft="16dp" />

<TextView android:text="@string/text"

android:layout_width="fill_parent" android:layout_height="wrap_content"

android:layout_centerVertical="true" android:textColor="#333333"

android:textSize="16sp" android:layout_marginLeft="38dp" />

<ImageView android:src="@drawable/icon_arrow_right"

android:layout_width="wrap_content" android:layout_height="wrap_content"

android:layout_centerVertical="true" android:layout_alignParentRight="true"

android:layout_marginRight="10dp" />

</RelativeLayout>

selector代码如下：<?xml version="1.0" encoding="utf-8"?>

<selector xmlns:android="http://schemas.android.com/apk/res/android">

<item android:state_pressed="false" android:drawable="@drawable/list_item" />

<item android:state_pressed="true" android:drawable="@drawable/list_item_pressed" />

</selector>

写到这个时候我以为那个RelativeLayout在ontouch的时候就会出现我想要的交互，但是木有！当我在对应的JAVA类中给那个RelativeLayout注册了setOnClickListener事件后交互就有了。不知道GOOGLE为什么这样设计，不过仔细想想也有道理，如果没有相应的事件，为什么要交互呢！