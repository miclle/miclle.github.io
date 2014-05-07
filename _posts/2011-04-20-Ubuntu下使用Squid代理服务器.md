---
layout: post
title:  "Ubuntu下使用Squid代理服务器"
date:   2011-04-20 03:35:09
categories: [Linux]
tags: [Linux, Ubuntu, Squid, 代理, 宽带, 光纤, 电信, 吭爹]
---

小区宽带升级成了光纤，2M变成了10M，爽！不过很吭爹的是，只能连四能PC，再连就不能上外网了，日啊！电信你大爷，你就是李莲英！

人民群众是智慧滴！GOOGLE了一把找到解决办法：

我这有一台Ubuntu的内网服务器，可以通过Squid代理服务器使其它PC上网，

安装：

root@ubuntu:~$ apt-get install squid

root@ubuntu:~$ vim /etc/squid/squid.conf

/INSERT YOUR OWN RULE(S) 找到  大概在671行的样子

# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS

# Example rule allowing access from your local networks.

# Adapt localnet in the ACL section to list your (internal) IP networks

# from where browsing should be allowed

#http_access allow localnet

http_access allow localhost

# And finally deny all other access to this proxy

# http_access deny all #修改这个地方接受所有IP，当然也可以限定只允许一些IP

http_access allow all

退出保存!

执行:

root@ubuntu:~$ squid -z

root@ubuntu:~$ /etc/init.d/squid reload

root@ubuntu:~$ /etc/init.d/squid restart

root@ubuntu:~$ squid -k parse

按教程来了这几步，好像没有生效，后来重启了一下就可以用了！

在其它PC上就可以设置代理，代理IP是刚刚设置代理服务器的网IP，端口是默认的3128

其它命令：

root@ubuntu:~$ squid (后台启动)

root@ubuntu:~$ squid -k shutdown (关掉代理)