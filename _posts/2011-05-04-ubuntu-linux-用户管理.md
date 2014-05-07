---
layout: post
title:  "ubuntu linux 用户管理"
date:   2011-05-04 05:33:27
categories: [Linux]
tags: [Linux, Ubuntu]
---

useradd 创建一个新的用户

groupadd 组名 创建一个新的组

passwd 用户名 为用户创建密码

passwd -d 用户名 删除用户密码也能登陆

passwd -l 用户名 锁定账号密码

passwd -u 用户名 解锁账号密码

passwd -S 用户名 查询账号密码

usermod -l 新用户名 老用户名 为用户改名

usermod -L 要锁定用户名 锁定用户登陆

usermod -U 解锁用户名 解锁用户登陆

usermod -u 用户名 改变用户UID

userdel–r 用户名 删除用户一切

groupmod -n 新用户名 老用户名 为组改名

groupmod -g 组名 改变组GID

groupdel 组名 先应删它的用户 删除组

gpasswd -a 用户名 组名 增加用户到组

id 用户名 查用户信息Example:1、输入用户管理的命令，新建用户（以test为例）：useradd test修改 test 用户的密码：passwd test2、将新用户添加到管理组：gpasswd -a test admin3、给 test 用户创建自己的目录：cd /homemkdir testchown test /home/test