---
author: wdmcja
comments: true
date: 2013-06-20 01:16:56+00:00
layout: post
slug: init%e5%90%af%e5%8a%a8%e7%ad%89%e7%ba%a7%e8%ae%be%e7%bd%ae
title: init启动等级设置
wordpress_id: 36
categories:
- linux
tags:
- etc
- linux
- 启动
---

 在linux下的init启动顺序是先/etc/init.d/rcS,再由其到rc?.d顺序执行，但其到rc?.d的启动级别是有区别的，该设置是在/etc/inittab文件中的：


{% highlight ruby %}
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:3:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.

z6:6:respawn:/sbin/sulogin

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  :::
#

T0:12345:respawn:/sbin/getty -L ttyS0 115200 vt100
#con:2345:respawn:/sbin/getty 115200 console
#con:2345:respawn:/sbin/mingetty --autologin root console

#1:2345:respawn:/sbin/getty 115200 tty1

#S0:2345:respawn:/sbin/getty 115200 ttyS0
#S1:2345:respawn:/sbin/getty 115200 ttyS1
#S2:2345:respawn:/sbin/getty 115200 ttyS2
{% endhighlight %}


id:3:initdefault:  指定了从等级3启动，即从rc3.d中启动

