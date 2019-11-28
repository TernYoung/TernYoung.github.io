---
title: jsDelivr+Github搭建免费CDN
date: 2019-11-28 19:17:36
tags:
	- CDN
	- jsDelivr
	- Github
categories:
	- 技术
author: Tern
authorLink: cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: CDN
description: jsDelivr+Github搭建免费CDN
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic020.jpg
---



# 什么是CDN？

> CDN的全称是Content Delivery Network，即内容分发网络。CDN是构建在网络之上的内容分发网络，依靠部署在各地的边缘服务器，通过中心平台的负载均衡、内容分发、调度等功能模块，使用户就近获取所需内容，降低网络拥塞，提高用户访问响应速度和命中率。CDN的关键技术主要有内容存储和分发技术。——百度百科

降维幼儿园化解释：

>  放在Github的资源在国内加载速度比较慢，因此需要使用CDN加速来优化网站打开速度，jsDelivr + Github便是免费且好用的CDN，非常适合博客网站使用。 

# 搭建CDN的步骤

1. 新建GitHub仓库

2. 克隆GitHub仓库到本地:`git clone 仓库地址`

3. 上传资源:`git add.` `git commit -m "first commit"` `git push`

4. 发布仓库：在仓库页面点 `releases` 自定义版本号发布

5. 通过jsDelivr引用资源：

   > 使用方法：https://cdn.jsdelivr.net/gh/你的用户名/你的仓库名@发布的版本号/文件路径 
   >
   > 例：https://cdn.jsdelivr.net/gh/TernYoung/nicePicture@1.1/smallPic/pic020.jpg
   >
   > 注意： 版本号不是必需的，是为了区分新旧资源，如果不使用版本号，将会直接引用最新资源
   >
   > 还可以使用某个范围内的版本，查看所有资源等，具体使用方法如下： 
   >
   > *  // 加载任何Github发布、提交或分支
   >    https://cdn.jsdelivr.net/gh/user/repo@version/file 
   > *  // 加载 jQuery v3.2.1
   >    https://cdn.jsdelivr.net/gh/jquery/jquery@3.2.1/dist/jquery.min.js 
   > * // 使用版本范围而不是特定版本
   >   https://cdn.jsdelivr.net/gh/jquery/jquery@3.2/dist/jquery.min.js
   >   https://cdn.jsdelivr.net/gh/jquery/jquery@3/dist/jquery.min.js
   > *  // 完全省略该版本以获取最新版本
   >    https://cdn.jsdelivr.net/gh/jquery/jquery/dist/jquery.min.js 
   > *  // 将“.min”添加到任何JS/CSS文件中以获取缩小版本，如果不存在，将为会自动生成
   >    https://cdn.jsdelivr.net/gh/jquery/jquery@3.2.1/src/core.min.js 
   > *  // 在末尾添加 / 以获取资源目录列表
   >    https://cdn.jsdelivr.net/gh/jquery/jquery/ 

   