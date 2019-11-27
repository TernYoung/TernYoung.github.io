---
title: Ubuntu下安装QQ
date: 2019-11-27 20:35:36
tags:
	- Linux
	- Ubuntu
	- QQ
categories:
	- 技术
author: Tern
authorLink: cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: Ubuntu
description: Ubuntu下安装QQ
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic027.jpg
---


## 一、安装deepin-wine环境

​	进入https://gitee.com/wszqkzqk/deepin-wine-for-ubuntu 页面下载zip包（或用git方式克隆），解压到本地文件夹，在文件夹目录下打开终端，输入如下命令，一键安装：

`sudo sh install.sh`

## 二、下载容器

在 http://mirrors.aliyun.com/deepin/pool/non-free/d/ 中下载想要的容器，点击deb安装即可。以下为推荐容器:

>QQ：http://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.com.qq.im/
TIM：http://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.com.qq.office/
QQ轻聊版：http://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.com.qq.im.light/
微信：http://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.com.wechat/
Foxmail：http://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.com.foxmail/
百度网盘：http://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.com.baidu.pan/
360压缩：http://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.cn.360.yasuo

进入相关下载页面，选择deb文件，下载下来


## 三、安装QQ

进入deb文件所在目录打开终端，输入命令如下：

`sudo dpkg -i deepin.com.qq.im_8.9.19983deepin23_i386.deb`

## 四、Ubuntu 18.04 Gnome桌面显示传统托盘图标

安装TopIconPlus的gnome-shell扩展，命令：

`sudo apt-get install gnome-shell-extension-top-icons-plus gnome-tweaks`

然后用gnome-tweaks开启这个扩展。

`gonme-tweaks`

