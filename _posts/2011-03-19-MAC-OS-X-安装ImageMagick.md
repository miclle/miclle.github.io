---
layout: post
title:  "MAC OS X 安装ImageMagick"
date:   2011-03-19 12:41:08
categories: [MAC]
tags: [MAC, ImageMagick, brew]
---

命令：brew install ImageMagick

Zheng-MicllematoMacBook-Pro:~ zhengmiclle$ brew install ImageMagick

Warning: It appears you have MacPorts or Fink installed.

Software installed with MacPorts and Fink are known to cause problems.

If you experience issues try uninstalling these tools.

==> Checking out https://www.imagemagick.org/subversion/ImageMagick/trunk

==> ./configure --disable-osx-universal-binary --without-perl --prefix=/usr/local/Cellar/imagemagick/6.6.4-5 --disable-dependency-tracking --enable-shared -

==> make install

==> Caveats

Because ImageMagick likes to remove tarballs, we're downloading their

stable release from their SVN repo instead. But they only serve the

repo over HTTPS, and have an untrusted certificate, so we auto-accept

this certificate for you.

If this bothers you, open a ticket with ImageMagick to fix their cert.

Some tools will complain if the ghostscript fonts are not installed in:

  /usr/local/share/ghostscript/fonts

==> Summary

/usr/local/Cellar/imagemagick/6.6.4-5: 1288 files, 32M, built in 2.6 minutes

Zheng-MicllematoMacBook-Pro:~ zhengmiclle$

在Checking out之前可能还有去下载安装几个依赖包