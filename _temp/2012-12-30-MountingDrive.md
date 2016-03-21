---
layout: post
title: Mounting a drive in Ubuntu 
tags: Ubuntu
category: Tech
---
Something that took me a while to figure out was if you have a secondary or external drive, you need to mount it if you want it to be accessible in Ubuntu. This is what worked for me...

#### sudo mount /dev/sdb1 /media/Storage -t ntfs -o nls=utf8,umask=0222
