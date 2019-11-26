---
title: Chocolatey
date: 2019-10-10 18:43:00
tags:
	- 包管理工具
	- windows
categories: 技术
author: Tern
authorLink: www.cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: Chocolatey
description: Win下包管理工具
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic018.jpg
---

### win10下安装Chocolatey

1. Open `PowerShell` (Tips:You can press `win+x` and then press  `a` to open `PowerShell`)

2. Run `Get-ExecutionPolicy`. If it returns `Restricted`, then run `Set-ExecutionPolicy AllSigned` or `Set-ExecutionPolicy Bypass -Scope Process`.

3. Now run the following command:

```cmd
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

4. Wait a few seconds for the command to complete.
5. If you don't see any errors, you are ready to use Chocolatey! Type `choco` or `choco -?` now

### Chocolatey 使用方法

常用命令：

* 列出本地已安装的包 `choco list –local-only `
* 列出Windows系统已安装的软件 `choco list -li `
* 升级所有已安装的包 `choco upgrade all -y`
* 搜索包 `choco search something`
* 列出包 `choco list -lo`
* 安装包 `choco install 包名`
* 固定包版本 `choco pin 包名`
* 更新包 `choco upgrade 包名`
* 卸载包 `choco  uninstall 包名`

更改安装包路径：

1. 执行“开始/运行”命令（或者WIN + R），输入“regedit”，打开注册表。
2. 展开注册表到下面的分支[HKEY＿LOCAL＿MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion]，在右侧窗口中找到名为“ProgramFilesDir”的字符串，双击把数值“C:\Program Files”修改为“D：\ProgramFiles”，确定退出后,即可更改常用软件的安装路径了。

