---
layout: post
title:  "box-shadow"
date:   2011-09-19 08:19:28
categories: [CSS3]
tags: [CSS3, box-shadow]
---

box-shadow: 阴影类型 X轴位移 Y轴位移 阴影大小 阴影扩展 阴影颜色当不设阴影类型时，默认为投影效果；当设为inset时，为内阴影效果。X轴和Y轴位移不等同但类似于photoshop里面的”角度”和”位置。阴影大小、扩展、颜色和Photoshop里面的都同理。img{box-shadow:0 0 10px #000;}颜色值可以使用RGBA值，RGBA值多了一个Alpha透明值，可以控制阴影的透明度img{box-shadow:0 0 10px rgba(0, 0, 0, 0.5)}firefox通过私有属性-moz-box-shadow支持Safari和Chrome通过私有属性-webkit-box-shadow支持img{  box-shadow:0 0 10px rgba(0, 0, 0, 0.5)  -webkit-box-shadow:0 0 10px rgba(0, 0, 0, 0.5)  -moz-box-shadow:0 0 10px rgba(0, 0, 0, 0.5)}box-shadow可以同时使用多次img{  box-shadow:-10px 0 10px red,   box-shadow:10px 0 10px blue,  box-shadow:0 -10px 10px yellow,  box-shadow:0 10px 10px green}