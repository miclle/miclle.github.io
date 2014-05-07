---
layout: post
title:  "Online Markdown Editor (GitHub Flavored)"
date:   2013-06-13 05:28:27
---

在重构自己Blog时，一直想要做一个实时的Markdown预览功能，类似于Mou http://mouapp.com/ 的效果，但不想通过后台解析，那样效率太低，最合适的方式当然是用JavaScript在客户端解析. 



初步效果如下：http://markdown.miclle.com/  

代码地址：https://github.com/miclle/Markdown-Editor



PS. CodeMirror 3.x在自动换行时对中文支持不太好，测试过2.x表现正常，3.x与2.x两个版本API有很大区别，个人Blog是用的2.38版本，这里使用版本为: 3.11 +版本