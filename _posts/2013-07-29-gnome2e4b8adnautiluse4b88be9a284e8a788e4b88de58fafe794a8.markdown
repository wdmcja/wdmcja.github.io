---
author: wdmcja
comments: true
date: 2013-07-29 09:28:03+00:00
layout: post
slug: gnome2%e4%b8%adnautilus%e4%b8%8b%e9%a2%84%e8%a7%88%e4%b8%8d%e5%8f%af%e7%94%a8
title: gnome2中nautilus下预览不可用
wordpress_id: 80
categories:
- linux
tags:
- gnome
- linux
---

   在gnome2中遇到了一个问题，就是预览没有办法用，用了很多办法还是找不到问题。而且在打开预览功能后，在~/.thumbnails下也找到了该图片的预览缩略图，只是还是没有办法显示。
    后来发现在~/.cache下也应该有一个thumbnails的文件夹，做了一个链接过去，可以正常显示了
