---
layout: post
title:  "用JavaScript获取选中的文字"
date:   2011-02-16 09:00:39
categories: [JavaScript]
tags: [JavaScript, jQuery]
---

function getSelectText() {

    return document.selection && document.selection.createRange().text || window.getSelection && window.getSelection() || document.getSelection && document.getSelection() || '';

}

支持IE6、Firefox和Chrome

原文：

[用JavaScript获取选中的文字](http://www.keakon.net/2009/06/20/%E7%94%A8JavaScript%E8%8E%B7%E5%8F%96%E9%80%89%E4%B8%AD%E7%9A%84%E6%96%87%E5%AD%97)

参考：

[获取鼠标选择的文本内容之JavaScript代码](http://www.cncmm.com/blog,bid-29.html)

参考：

[Use JavaScript and jQuery to Get User Selected Text, and then Do Something (Useful?) With It](http://mark.koli.ch/2009/09/use-javascript-and-jquery-to-get-user-selected-text.html)