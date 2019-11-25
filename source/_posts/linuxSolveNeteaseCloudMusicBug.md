---
title: Linux 网易云音乐的一些Bug
author: Tern
authorLink: cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
date: 2019-11-21 20:38:45
comments: true
keywords: 网易云音乐
description: 修复Linux 网易云音乐的一些Bug
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/Wallpapers/a3.png
categories: 
	- 技术
tags: 
    - Linux
    - 网易云音乐
---



## 网易云音乐突然不能打开，只能在终端打开。

1. 输入命令：

```linux
sudo gedit /etc/sudoers
```


再最后面加一行：


```linux
用户名 ALL = NOPASSWD: /usr/bin/netease-cloud-music  注：用户名为当前登录用户名
```

2. 输入命令：

```linux
sudo gedit /usr/share/applications/netease-cloud-music.desktop 
```

修改`Exec=netease-cloud-music %U` 为 `Exec=sudo netease-cloud-music %U`

这样点击网易云音乐图标就可直接打开了。

## 网易云音乐不能输入中文

我用的是 `fcitx` `搜狗`

1. 输入命令：

```linux
sudo gedit /etc/sudoers_env
```

在新建的文件中加入下面三行代码：

```linux
GTK_IM_MODULE=xim
QT_IM_MODULE=xim
QT4_IM_MODULE=xim
```

保存退出

2. 输入命令：

```linux
sudo visudo
```

在最后添加：

```linux
Defaults env_keep += "XMODIFIERS"
Defaults env_file="/etc/sudoers_env"
```

保存重启网易云音乐

