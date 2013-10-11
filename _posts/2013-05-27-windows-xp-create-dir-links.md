---
layout: post
title: "windows xp create dir links"
description: "junction"
category: tools
tags: [windows, xp, junction]
---
{% include JB/setup %}

###### windows xp下创建符号链接
  今天给女友的电脑设置dropbox同步的时候遇到一个问题，就是她想同步指定的文件夹，   
当时立马就想到了windows中的mklink，可惜她用的是悲剧的xp系统，去网上找了下，找到一个junction的东东。   
[点此下载](http://technet.microsoft.com/en-us/sysinternals/bb896768.aspx "点此下载")   
使用方法如下：
 1.	下载刚才那个文件，并解压到c:/windows/system32
 2. 打开cmd，进入比如D盘，输入`junction d:/linkdir "d:/srcdir"`
 3. 删除这个链接可以直接删除链接后的文件夹，也可以用`junction -d d:/linkdir`