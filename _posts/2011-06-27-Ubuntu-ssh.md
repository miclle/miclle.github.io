---
layout: post
title:  "Ubuntu ssh"
date:   2011-06-27 04:50:25
categories: [Linux]
tags: [Linux, ssh, Ubuntu]
---

安装：sudo apt-get install openssh-server开启：/etc/init.d/ssh start确认sshserver启动：ps -e |grep ssh配置：/etc/ssh/sshd_config重启：/etc/init.d/ssh resar连接：ssh root@192.168.1.1