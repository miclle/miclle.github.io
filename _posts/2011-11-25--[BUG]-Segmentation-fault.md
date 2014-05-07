---
layout: post
title:  " [BUG] Segmentation fault"
date:   2011-11-25 03:24:01
categories: [Ruby On Rails, MAC]
tags: [ruby, rails, gem, MAC, RVM, Xcode]
---

在用RVM安装ruby 1.8.7后，安装gem时老是出现下面这个错误.rvm/rubies/ruby-1.8.7-p334/lib/ruby/1.8/timeout.rb:60: [BUG] Segmentation fault试了几次无果，后来查到这篇文章 http://jalada.co.uk/2011/07/24/lion-rvm-and-ruby-1-8-7-woes.html$ rvm remove 1.8.7

$ rvm remove 1.8.7 --gems

$ rvm remove 1.8.7 --archive

$ CC=/usr/bin/gcc-4.2 rvm install 1.8.7我MAC Xcode版本是4.2.1