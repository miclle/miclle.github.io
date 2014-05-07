---
layout: post
title:  "homebrew — Mac OS X 下新的软件包管理工具（转载）"
date:   2011-03-19 09:18:49
categories: [MAC]
tags: [MAC, homebrew]
---

安装：

首先，Homebrew 的原则是“No sudo”，也就是说，既然 Mac OS X (client 版本) 绝大部分情况下都是归你这个有管理员权限的用户，为什么在自己的 /usr/local 下安装程序还需要 sudo 呢？所以，首先：

sudo chown -R `whoami` /usr/local

然后可以正式开始安装，我推荐的安装方式是先用 git-osx-installer 装上 git，然后用 git 安装：

cd /usr/local

git init

git remote add origin git://github.com/mxcl/homebrew.git

git pull origin master

这么做的实际作用是把你的 /usr/local 目录变成了一个本地 git 仓库，只不过这个仓库只跟踪跟 Homebrew 相关的更新，并不影响任何其他软件的安装。

这样安装会在 /usr/local 下创建 Library 这个目录，然后在 /usr/local/bin 中加入 brew 这个 ruby 脚本。

使用：

安装完毕，下面就可以试试了：

brew search

这个命令用来搜索所有可以通过 homebrew 安装的软件，不带任何参数的时候就是列出所有的。可以看到数量已经不少了。

下面就是选择安装，比如我想安装 unrar：

$ brew search rar

gnu-scientific-library     unrar

$ brew install unrar

Warning: It appears you have Macports or Fink installed

Although, unlikely, this can break builds or cause obscure runtime issues.

If you experience problems try uninstalling these tools.

/usr/local/Library/Formula/unrar.rb:3: warning: already initialized constant ALL_CPP

==> Downloading http://www.rarlab.com/rar/unrarsrc-3.9.4.tar.gz

######################################################################## 100.0%

==> g++ -O4 -march=core2 -mmmx -msse3 -w -pipe -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE all.cpp -o unrar

/usr/local/Cellar/unrar/3.9.4: 3 files, 320K, built in 13 seconds

可以看到，unrar 被安装到了 /usr/local/Cellar/unrar/3.9.4 这个目录下，但这样我们访问起来显然很不方便，所以 Homebrew 会在 /usr/local/bin 下面创建到 unrar 程序的符号链接，如果安装的是库之类的，也会对应在 /usr/local/lib 这样的目录下创建符号链接。所以这是一套类似 GoboLinux 的软件管理方式。

安装后就可以用 list 命令列出：

$ brew list

pkg-config  unrar

更新：

如果用了一段时间，需要更新同步上游的 Formula，可以简单地：

$ brew update

From git://github.com/mxcl/homebrew

 * branch            master     -> FETCH_HEAD

Updated Homebrew from 60600885 to 60600885.

No formulae were updated.

Homebrew 会通过 git 完成同步。

原文：

[http://blog.jjgod.org/2009/12/21/homebrew-package-management/](http://blog.jjgod.org/2009/12/21/homebrew-package-management/)