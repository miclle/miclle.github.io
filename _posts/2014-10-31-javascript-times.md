---
layout: post
title:  "用 JavaScript 实现 ruby times 方法"
date:   2014-10-31 11:12:00
categories: [post]
tags: [JavaScript, ruby, times]
---


##JavaScript

```
Number.prototype.times = function(fn) {
  var times = this.valueOf();
  while(times && times > 0){
  	fn();
  	times--;
  }  
};

5..times(function(){
  console.log('Hello World!');
});
```


##CoffeeScript

```
Number::times = (fn) ->
  do fn for [1..@valueOf()] if @valueOf()
  return
  
5.times -> console.log 'Hello World!'
```

