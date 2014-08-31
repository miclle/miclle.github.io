---
layout: post
title:  "JavaScript Object Prototypes"
date:   2014-09-01 00:00:00
categories: [JavaScript]
tags: [JavaScript, Object, Prototype]
---

有这样的需求，比如要把 "Hello World" 这个字符串变成 "H e l l o  W o r l d" 这个，在每个字母间增加一个空格。

一般的做法，比如这样： "Hello World".split('').join(' '); 先将字符串切割成数组，然后再用空格连接。

为了实现通用，也许我们要定义为一个函数：


```js
function spacify(str){
  return str.split('').join(' ');
}
```


如果我们希望这个函数直接可以更简单一点使用，这样用 "Hello World".spacify() ，那我们需要将这个方法放到 String 对象上，如：


```js
String.prototype.spacify = function(){
  return this.split('').join(' ');
}
```


prototype 表示 Object 的原型对象，在 JavaString 中所有对象都由 Object 继承而来，通过 probotype 可以给对象增加方法和属性。

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype

