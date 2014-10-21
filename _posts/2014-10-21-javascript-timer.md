---
layout: post
title:  "JavaScript Timer"
date:   2014-10-21 23:02:00
categories: []
tags: [JavaScript, setTimeout, setInterval, requestAnimationFrame, setImmediate]
---

#JavaScript 定时器

在 JavaScript 中说到定时器，最常用的就两个： `setTimeout()` 和 `setInterval()` 这两个函数，它们的内部运行机制完全一样，区别在于 `setTimeout` 指定的代码是一次性执行，`setInterval` 则为反复执行。

##setTimeout()
###语法
```
var timerID = window.setTimeout(func/code, delay);
```
 * timerID 是该延时操作的数字ID, 此ID随后可以用来作为clearTimeout方法的参数.
 * func 是你想要在delay毫秒之后执行的函数，code 在第二种语法,是指你想要在delay毫秒之后执行的代码 (使用该语法是不推荐的, 不推荐的原因和eval()一样)
 * delay 是延迟的毫秒数 (一秒等于1000毫秒),函数的调用会在该延迟之后发生.但是实际的延迟时间可能会稍长一点.
 

###例子
```
function test(text) {
	console.log("print: " + text);
}
setTimeout(test, 1000);
```

```
// 使用匿名函数来传递参数
function test(text) {
	console.log("print:" + text);
}
setTimeout(function(){
	test("Hello world!");
}, 1000);
```

```
// 不推荐的用法
setTimeout("test('Hello world!')", 1000);
```

在 setTimeout 的回调函数或匿名函数中要特别注意 this 的值在上下文中的变化。

#### delay 的延迟
如果将delay设为0，就表示当前代码执行完（执行栈清空）以后，立即执行（0毫秒间隔）指定的回调函数。

```
setTimeout(function(){console.log(1);}, 0);
console.log(2);
```

在早期，JavaScript 的 callback 执行，是依赖 CPU 的中断来进行控制的，如果两个中断之间时间太短会导致，CPU 性能消耗很高，同时影响能耗，于是微软和英特公司为了解决这个问题，就约定每个中断之间的间隔是 15.6ms（64 fps）所以就是我们常见的约等于 16ms 的间隔。

现在 HTML5 标准规定了 setTimeout() 的第二个参数的最小值（最短间隔），不得低于4毫秒，setTimeout的间隔缩短到了 4ms（250 fps）。

这个坑在我做 FFTS.IO 的时候被踩到，FFTS.IO 上传的效果需要用 canvas 做一个秒表，每秒钟需要去绘制一个圆，当时简单粗暴的这样写了:

```
setInterval(function(){
	ctx.arc(...)
},1)
```
每毫秒去绘制一个角度 (360/1000) 出来的效果总是要比实际时间长。于是将 delay 设置为 16，每次绘制角度 360/(1000/16) 这样才正常。当然也可以使用

```
requestAnimationFrame()
```

###requestAnimationFrame() 
requestAnimationFrame() 通常被调用的频率是每秒60次, 不仅仅可以解决中断调度的问题，还可以更加优化得统一管理动画单元里dom元素的repaint方式, 效果要好于setTimeout(), 但是 IE10 以下浏览器还不支持。

###setImmediate()
该方法最近刚刚被微软提出, 可能不会被w3c批准成为标准, 目前只有 Internet Explorer 10实现了该方法.
setImmediate大约0.16ms执行一次，fps超过6000。


参考链接
https://developer.mozilla.org/zh-CN/docs/DOM/window.setTimeout
https://developer.mozilla.org/zh-CN/docs/Web/API/Window.setInterval
https://developer.mozilla.org/zh-CN/docs/Web/API/window.requestAnimationFrame
https://developer.mozilla.org/zh-CN/docs/Web/API/window.setImmediate
