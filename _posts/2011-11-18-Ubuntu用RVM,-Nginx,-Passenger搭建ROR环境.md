---
layout: post
title:  "Ubuntu用RVM, Nginx, Passenger搭建ROR环境"
date:   2011-11-18 19:10:41
categories: [Linux, Ruby On Rails]
tags: [Linux, nginx, ruby, rails, Ubuntu, Passenger]
---

参考：https://rvm.beginrescueend.com/rvm/install/http://ruby-china.org/wiki/install_ruby_guidehttp://blog.ninjahideout.com/posts/a-guide-to-a-nginx-passenger-and-rvm-server以前步骤我都是在root下进行安装开发包$ apt-get install wget vim build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libxml2-dev libxslt-dev autoconf automake libtool imagemagick libpcre3-dev安装RVM$ bash < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)RVM会安装到 /usr/local/rvm/ 下

vim .bashrc

#[ -z "$PS1" ] && return 

if [[ -n "$PS1" ]]; then

#add

. /usr/local/rvm/scripts/rvm

source .bashrc

$ rvm -v

rvm 1.9.2 by Wayne E. Seguin (wayneeseguin@gmail.com) [https://rvm.beginrescueend.com/]用 RVM 安装 Ruby 环境$ rvm pkg install readline

$ rvm install 1.9.3 --with-readline-dir=$rvm_path/usr

$ rvm 1.9.3 --default

$ ruby -v

ruby 1.9.3p0 (2011-10-30 revision 33570) [x86_64-linux]

$ gem -v

1.8.10

安装 Rails$ gem install railsbundler好像默认就有了安装 passengergem install passenger

安装 nginxrvmsudo passenger-install-nginx-module这个步骤需要一些required softwares，可以按照提示完成测试nginx$ nginx -v

nginx: nginx version: nginx/1.0.6检查nginx.confhttp {

# load passenger

passenger_root /usr/local/rvm/gems/ruby-1.9.3-p0/gems/passenger-3.0.9;

passenger_ruby /usr/local/rvm/wrappers/ruby-1.9.3-p0/ruby;启动 Nginx$ nginx