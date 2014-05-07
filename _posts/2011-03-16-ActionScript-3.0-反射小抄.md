---
layout: post
title:  "ActionScript 3.0 反射小抄"
date:   2011-03-16 06:50:14
categories: [前端, ActionScript]
tags: [AS, 反射, ActionScript]
---

flash.utils.getQualifiedClassName获取实例的类名

var sprite:Sprite = new Sprite();

trace(getQualifiedClassName(sprite));

// 输出"flash.display::Sprite"

flash.utils.getQualifiedSuperclassName 获取超类的名称：

trace(getQualifiedSuperclassName(sprite));

// 输出"flash.display::DisplayObjectContainer"

flash.utils.getDefinitionByName通过类名字符串获取类的原型(类对象引用)

var Tmp = getDefinitionByName("flash.display.Sprite");

var spr = new Tmp;

trace(spr is Sprite);

//输出 true

flash.utils.describeType 可以获取非常详细的类的信息：

trace(describeType(new Sprite));