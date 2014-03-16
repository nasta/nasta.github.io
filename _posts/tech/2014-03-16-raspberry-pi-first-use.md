---
layout: post
title:  "树莓派初体验"
date:   2014-03-16
comments: true
categories: 
tags: ["raspberry pi"]
---

入手
====

最近诸事不顺，心情不爽，遂决定败个RPi折腾折腾。刚好某坛有人180大洋出一UK B版派，果断入手之。

经过两天的等待，买的SD卡和RPi都

安装系统
========

下载[最新的Arch镜像](http://downloads.raspberrypi.org/arch_latest)

解压镜像

    unzip ArchLinuxARM-2014.01-rpi.img.zip

写入系统镜像

	dd bs=4M if=ArchLinuxARM-2014.01-rpi.img of=/dev/sdc

启动RPi，SSH连接
================

由于没有无线路由和外接显示器，只能用有线连接+SSH了。

先给笔记本上的Archlinux安装dhcpd服务器

	sudo pacman -S dhcp

编辑/etc/dhcpd.conf

    option domain-name-servers 8.8.8.8;
    option subnet-mask 255.255.255.0;
    option routers 192.168.126.252;

    subnet 192.168.126.0 netmask 255.255.255.0 {
        range 192.168.126.240 192.168.126.250;
    }

连接好树莓派，启动～

在笔记本上ping树莓派，wait for network ready

    ping 192.168.126.240

大概十几秒的时间，ping有成功提示了，果断ssh

    ssh root@192.168.126.240

等等，密码是多少？现在才想起来被遗忘的[Wiki](http://elinux.org/ArchLinux_Install_Guide)君。Wiki君大方的告诉俺密码是root，哦也，first blood~

配置系统
========

Wiki君的话不能不听，不过俺好像只改了时区

	rm /etc/localtime
    ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
    echo "Asia/Shanghai" > /etc/timezone

添加清华源，编辑`/etc/pacman.d/mirrorlist`，在`Server = http://mirror.archlinuxarm.org/armv6h/$repo`一行的上面添加

    Server = http://mirrors.tuna.tsinghua.edu.cn/archlinuxarm/armv6h/$repo

更新一下系统

    pacman -Syy

系统自带软件也太少了吧，装一些必备的软件吧

    pacman -S sudo base-devel bash-completion vim

安装内核头文件，方便以后编译模块

    pacman -S linux-raspberrypi-headers

后记
====

测试了编译驱动，用了接近20分钟，bash的自动不全速度也差强人意。习惯了PC流畅的速度，感觉RPi的性能还是偏弱的。不过700M的CPU，也不能期望太多，应付日常应用应该也是足够的。
