---
layout: post
title:  "shutdown --help"
date:   2011-04-26 06:10:43
categories: [Linux]
tags: [Linux]
---

miclle@ubuntu:~$ shutdown --help

Usage: shutdown [OPTION]... 时间 [信息]

使系统关闭。

Options:

-r    reboot after shutdown

-h    halt or power off after shutdown

-H    halt after shutdown (implies -h)

-P    power off after shutdown (implies -h)

-c    cancel a running shutdown

-k    only send warnings, don't shutdown

-q, --quiet   reduce output to errors only

-v, --verbose   increase output to include informational messages

--help   display this help and exit

--version   output version information and exit时间 可以使用不同的格式，最常用的是简单的一个单词 “now”，其使系统立即关闭。  其它可用的格式有 +m ，此 m是关机前等待的分钟数；hh:mm 其指定以 24 小时制中的时间。已登录的用户被一条发送到他们终端的一条消息警告，您可以包含一条可选的 消息 到此项中。  使用 -k选项可以发送警告而不真的关机。如果给出 时间 ，此命令将留在前端指导关机发生。  可以使用 Control-C 取消它，或者被其他用户以 -c 选项取消。系统默认进入维护状态 (单用户) 模式，你可以使用 -r 或 -h 更改此行为，其分别指定系统重启或关闭。-h 选项可以进一步由 -H 或 -P来指定伺候是关机还是切断电源。  默认动作由 shutdown 脚本决定。