---
title: Ubuntu修改swap分区大小
date: 2019-12-01 15:27:23
tags: 
	- Ubuntu
	- swap分区
categories:
	- 技术
author: Tern
authorLink: www.cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: swap分区
description: Ubuntu修改swap分区大小
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic095.jpg
---



## 一、Linux的swap分区简介

> ​	Swap分区，即[交换区](https://baike.baidu.com/item/交换区)，系统在[物理内存](https://baike.baidu.com/item/物理内存)（这里应该是运行内存）不够时，与Swap进行交换。 把物理内存中的一部分空间释放出来，以供当前运行的程序使用。那些被释放的空间可能来自一些很长时间没有什么操作的程序，这些被释放的空间被临时保存到Swap分区中，等到那些程序要运行时，再从Swap分区中恢复保存的数据到内存中。 

## 二、Linux 的 swap 空间要设置多大？

官方的建议：

| Amount of RAM in the system | Recommended swap space     | Recommended swap space if allowing for hibernation |
| :---------------------------: | :--------------------------: | :--------------------------------------------------: |
| ⩽ 2GB                       | 2 times the amount of RAM  | 3 times the amount of RAM                          |
| \> 2GB – 8GB                | Equal to the amount of RAM | 2 times the amount of RAM                          |
| \> 8GB – 64GB               | At least 4 GB              | 1.5 times the amount of RAM                        |
| \> 64GB                     | At least 4 GB              | Hibernation not recommended                        |

*Tips:Hiberation(休眠功能)*

以下是Ubuntu的建议：

| RAM(GB) | No hibernation | With Hibernation | Maximum |
| :-------: | :--------------: | :----------------: | :-------: |
| 1       | 1              | 2                | 2       |
| 2       | 1              | 3                | 4       |
| 3       | 2              | 5                | 6       |
| 4       | 2              | 6                | 8       |
| 5       | 2              | 7                | 10      |
| 6       | 2              | 8                | 12      |
| 8       | 3              | 11               | 16      |
| 12      | 3              | 15               | 24      |
| 16      | 4              | 20               | 32      |
| 24      | 5              | 29               | 48      |
| 32      | 6              | 38               | 64      |
| 64      | 8              | 72               | 128     |
| 128     | 11             | 139              | 256     |

## 三、Ubuntu 修改 swap 分区大小

### 1.首先用命令 `free -m` 查看系统内的 swap 分区大小

### 2.增加 swap 分区大小

```shell
#个人建议在根目录下
cd /
mkdir swap
cd swap
sudo dd if=/dev/zero of=swapfile bs=1M count=2k #最终大小为bs*conut,所以建议n就count=nk,这步比较慢和卡，等会，成功了会提示并且在swap文件夹下会多一个swapfile
sudo mkswap swapfile #把生成的文件转换成 swap 文件 
swapon swapfile #挂载 swap 文件,挂载后可再次查看 free -m
```

### 3、重启后查看swap分区，发现又变回去了

重新激活swap分区 `sudo swapon /swap/swapfile`

将其写入 /etc/fstab 文件

```shell
sudo nano /etc/fstab

#增加以下两行：

(add swap space on /swap/swapfile)
 /swap/swapfile                          /swap           swap    defaults        0       0
```

关机重启确认swap大小

### 4、减少 swap 分区大小

```shell
sudo swapoff swapfile # 进入swap文件目录，卸载 swap 文件，卸载后可以删除，这样就减小了
```

