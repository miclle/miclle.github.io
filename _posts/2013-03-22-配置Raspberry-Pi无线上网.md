---
layout: post
title:  "配置Raspberry Pi无线上网"
date:   2013-03-22 12:12:04
---

入手Raspberry Pi有几天了，一直插根网络连到MAC上通过共享网络来连接网络，不是很方便。



网上有说可以用TP-LINK TL-WN725N迷你路由器来连接网络，便从京东上买了一个，然后悲剧的折腾开始。首先TL-WN725N在Raspberry Pi上并没有自带驱动，当然网上有解决方案，有人在drobox上提供了一个安装驱动的脚本，好吧，各种折腾后把脚本弄到了Raspberry Pi上，可惜运行失败，让我这Linux文盲很受挫，google到很多资料，找到一个[大牛](http://gutspot.com/2013/01/30/%E7%94%A8raspberry-pi%E5%88%B6%E4%BD%9C%E6%97%A0%E7%BA%BF%E8%B7%AF%E7%94%B1%E8%BF%87%E7%A8%8B%E7%9A%84%E6%9C%AD%E8%AE%B02-%E7%BC%96%E8%AF%918188eu%E8%8A%AF%E7%89%87%E7%9A%84%E6%97%A0%E7%BA%BF%E7%BD%91/)折腾的过程，更加迷茫了... 不过在文章结尾的时候看到一句：



>年后进了一个Tenda W311MI（主控是Ralink RT5370），RPi的固件中直接提供了驱动，省了手工编译安装驱动的麻烦。



第二天我又在京东上入了一个 `腾达（TENDA）W311MI 超级Mini无线USB网卡` 好吧，我比较败家!



买回来插到Raspberry Pi上启动后运行 `lsusb`



    pi@raspberrypi:~$ lsusb

    Bus 001 Device 002: ID 0424:9512 Standard Microsystems Corp.

    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

    Bus 001 Device 003: ID 0424:ec00 Standard Microsystems Corp.

    Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

    Bus 001 Device 005: ID 03eb:0902 Atmel Corp. 4-Port Hub

    Bus 001 Device 006: ID 062a:0000 Creative Labs Optical mouse

    Bus 001 Device 007: ID 413c:2003 Dell Computer Corp. Keyboard



其中`Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter`并是W311MI路由器，真好真省事早买这个就不会学浪费之前折腾的几个小时了



运行 `iwconfig`



    pi@raspberrypi:~$ iwconfig

    wlan0     IEEE 802.11bgn  ESSID:"TP-LINK_Z"

          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:27:19:78:B2:E8

          Bit Rate=54 Mb/s   Tx-Power=20 dBm

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:on

          Link Quality=43/70  Signal level=-67 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:22  Invalid misc:6   Missed beacon:0



    lo        no wireless extensions.



    eth0      no wireless extensions.



`wlan0` 就是你的无线网卡信息了



####接下来步骤：配置网络



修改/etc/network/interfaces



    auto lo



    iface lo inet loopback

    iface eth0 inet dhcp



    allow-hotplug wlan0

    iface wlan0 inet manual

    wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf



    iface default inet dhcp



网上说可以设置静态IP，我尝试了下可惜失败了:(



修改 /etc/wpa_supplicant/wpa_supplicant.conf



    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev

    update_config=1



    network={

      ssid="无线名称"

      psk="无线密码"

      proto=WPA

      key_mgmt=WPA-PSK

      pairwise=TKIP

      auth_alg=OPEN

    }



proto key_mgmt与pairwise的值与你无线网络的设置对应上即可



最后 `sudo reboot` 重启



运行`ifconfig -a`



    @raspberrypi:~$ ifconfig -a

    eth0      Link encap:Ethernet  HWaddr b8:27:eb:f8:c5:7f

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



    lo        Link encap:Local Loopback

          inet addr:127.0.0.1  Mask:255.0.0.0

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:8 errors:0 dropped:0 overruns:0 frame:0

          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0

          RX bytes:1104 (1.0 KiB)  TX bytes:1104 (1.0 KiB)



    wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c5:cc:6b

          inet addr:192.168.2.104  Bcast:255.255.255.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:958 errors:0 dropped:0 overruns:0 frame:0

          TX packets:368 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000

          RX bytes:172315 (168.2 KiB)  TX bytes:47919 (46.7 KiB)



Raspberry Pi的局域网IP为 `192.168.2.104` 然后我在MAC上就可以ssh远程登录了



####参考文章：



 * [用Raspberry Pi制作无线路由过程的札记2-编译8188eu芯片的无线网卡驱动和hostap](http://gutspot.com/2013/01/30/%E7%94%A8raspberry-pi%E5%88%B6%E4%BD%9C%E6%97%A0%E7%BA%BF%E8%B7%AF%E7%94%B1%E8%BF%87%E7%A8%8B%E7%9A%84%E6%9C%AD%E8%AE%B02-%E7%BC%96%E8%AF%918188eu%E8%8A%AF%E7%89%87%E7%9A%84%E6%97%A0%E7%BA%BF%E7%BD%91/’)

 * [Raspberry Pi快速上手教程](http://www.eeboard.com/tutorials/raspberry-pi%E5%BF%AB%E9%80%9F%E4%B8%8A%E6%89%8B%E6%95%99%E7%A8%8B/2/)

 * [How To: WiFi on your Raspberry PI](http://pingbin.com/2012/12/setup-wifi-raspberry-pi/)

 * [Raspberry Pi快速上手教程](http://www.eeboard.com/tutorials/raspberry-pi%E5%BF%AB%E9%80%9F%E4%B8%8A%E6%89%8B%E6%95%99%E7%A8%8B/2/)

 * [Set up your Raspberry Pi wireless network.](http://www.raspberrypi-tutorials.co.uk/set-raspberry-pi-wireless-network/)

 * [[原创]在树莓派上使用腾达(Tenda)W311MI迷你无线USB网卡(RT5370芯片)/Using Tenda W311MI mini wireless USB adapter(based on RT5370 chipset) on Raspberry Pi](http://www.codelast.com/?p=5393)





