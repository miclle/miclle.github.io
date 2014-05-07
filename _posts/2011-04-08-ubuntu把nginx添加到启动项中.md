---
layout: post
title:  "ubuntu把nginx添加到启动项中"
date:   2011-04-08 08:47:42
categories: [Linux, Ruby On Rails]
tags: [Linux, nginx, rails, vps, chkconfig]
---

网站用nginx在跑，网站经常疑似被挂掉，只因没钱买了个便宜的VPS，米国滴，经常被重启，为毛？米国也有G党？有木有？有木有？太坑爹了！

解决办法是把nginx添加到启动项中去，在 /etc/init.d/ 目录下添加 nginx 文件：

root@ubuntu: /etc/init.d/# vim nginx#! /bin/sh

# chkconfig: - 58 74

# description: nginx is the Nginx daemon. 

# Description: Startup script for nginx webserver on Debian. Place in /etc/init.d and

# run 'sudo update-rc.d nginx defaults', or use the appropriate command on your

# distro.

#

# Author: Ryan Norbauer

# Modified: Geoffrey Grosenbach http://topfunky.com

# Modified: David Krmpotic http://davidhq.com 

set -e 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

DESC="nginx daemon"

NAME=nginx

DAEMON=/usr/local/nginx/sbin/$NAME

CONFIGFILE=/usr/local/nginx/conf/nginx.conf 

PIDFILE=/usr/local/nginx/logs/$NAME.pid

SCRIPTNAME=/etc/init.d/$NAME 

# Gracefully exit if the package has been removed.

test -x $DAEMON || exit 0 

d_start() {

$DAEMON -c $CONFIGFILE || echo -en "\n already running"

} 

d_stop() {

kill -QUIT `cat $PIDFILE` || echo -en "\n not running"

} 

d_reload() {

kill -HUP `cat $PIDFILE` || echo -en "\n can't reload"

} 

case "$1" in

start)

echo -n "Starting $DESC: $NAME"

d_start

echo "."

;;

stop)

echo -n "Stopping $DESC: $NAME"

d_stop

echo "."

;;

reload)

echo -n "Reloading $DESC configuration..."

d_reload

echo "."

;;

restart)

echo -n "Restarting $DESC: $NAME"

d_stop

# One second might not be time enough for a daemon to stop,

# if this happens, d_start will fail (and dpkg will break if

# the package is being upgraded). Change the timeout if needed

# be, or change d_stop to have start-stop-daemon use --retry.

# Notice that using --retry slows down the shutdown process

# somewhat.

sleep 1

d_start

echo "."

;;

*)

echo "Usage: $SCRIPTNAME {start|stop|restart|reload}" >&2

exit 3

;;

esac 

exit 0

root@ubuntu: /etc/init.d/# chmod +x nginx

root@ubuntu: /etc/init.d/# update-rc.d nginx defaults

好像到这里就完事了...

查看一下

root@ubuntu: chkconfig --list

...

nginx                     0:off  1:off  2:on   3:on   4:on   5:on   6:off

...

相关链接：

[https://github.com/lxneng/confs/blob/master/ubuntu/etc/init.d/nginx](https://github.com/lxneng/confs/blob/master/ubuntu/etc/init.d/nginx)

[https://github.com/lxneng/confs/raw/master/ubuntu/etc/init.d/nginx](https://github.com/lxneng/confs/raw/master/ubuntu/etc/init.d/nginx)

[http://hi.baidu.com/nivrrex/blog/item/afb98c54a6f7a1143a29353e.html](http://hi.baidu.com/nivrrex/blog/item/afb98c54a6f7a1143a29353e.html)

感谢国家，感谢罗小能