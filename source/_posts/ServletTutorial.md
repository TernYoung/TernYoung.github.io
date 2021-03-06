---
title: Servlet教程
date: 2019-12-02 19:02:20
tags: 
	- Java
	- Jsp
	- Web开发
categories:
	- 技术
author: Tern
authorLink: www.cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: Servlet
description: Servlet教程
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic074.jpg
---



# Servlet教程

> 阅读本教程前需要了解的知识：
>
> 对 Java 编程语言有一个很好的理解。如果您对 web 应用程序和互联网如何工作的有基本的认识，将有助于您理解本教程。

## 一、Servlet简介

> Java Servlet 是运行在 Web 服务器或应用服务器上的程序，它是作为来自 Web 浏览器或其他 HTTP 客户端的请求和 HTTP 服务器上的数据库或应用程序之间的中间层。
>
> 使用 Servlet，您可以收集来自网页表单的用户输入，呈现来自数据库或者其他源的记录，还可以动态创建网页。
>
> Java Servlet 通常情况下与使用 CGI（Common Gateway Interface，公共网关接口）实现的程序可以达到异曲同工的效果。但是相比于 CGI，Servlet 有以下几点优势：
>
> - 性能明显更好。
>- Servlet 在 Web 服务器的地址空间内执行。这样它就没有必要再创建一个单独的进程来处理每个客户端请求。
> - Servlet 是独立于平台的，因为它们是用 Java 编写的。
>- 服务器上的 Java 安全管理器执行了一系列限制，以保护服务器计算机上的资源。因此，Servlet 是可信的。
> - Java 类库的全部功能对 Servlet 来说都是可用的。它可以通过 sockets 和 RMI 机制与 applets、数据库或其他软件进行交互。

Servlet 在 Web 应用程序中的位置：

![Servlet架构](https://www.runoob.com/wp-content/uploads/2014/07/servlet-arch.jpg)

>  Servlet 的任务：
>
> - 读取客户端（浏览器）发送的显式的数据。这包括网页上的 HTML 表单，或者也可以是来自 applet 或自定义的 HTTP 客户端程序的表单。
> - 读取客户端（浏览器）发送的隐式的 HTTP 请求数据。这包括 cookies、媒体类型和浏览器能理解的压缩格式等等。
> - 处理数据并生成结果。这个过程可能需要访问数据库，执行 RMI 或 CORBA 调用，调用 Web 服务，或者直接计算得出对应的响应。
> - 发送显式的数据（即文档）到客户端（浏览器）。该文档的格式可以是多种多样的，包括文本文件（HTML 或 XML）、二进制文件（GIF 图像）、Excel 等。
> - 发送隐式的 HTTP 响应到客户端（浏览器）。这包括告诉浏览器或其他客户端被返回的文档类型（例如 HTML），设置 cookies 和缓存参数，以及其他类似的任务。
>
> Servlet 包：
>
> Java Servlet 是运行在带有支持 Java Servlet 规范的解释器的 web 服务器上的 Java 类。
>
> Servlet 可以使用 **javax.servlet** 和 **javax.servlet.http** 包创建，它是 Java 企业版的标准组成部分，Java 企业版是支持大型开发项目的 Java 类库的扩展版本。
>
> 这些类实现 Java Servlet 和 JSP 规范。在写本教程的时候，二者相应的版本分别是 Java Servlet 2.5 和 JSP 2.1。
>
> Java Servlet 就像任何其他的 Java 类一样已经被创建和编译。在您安装 Servlet 包并把它们添加到您的计算机上的 Classpath 类路径中之后，您就可以通过 JDK 的 Java 编译器或任何其他编译器来编译 Servlet。



## 二、Servlet 生命周期

> Servlet 生命周期可被定义为从创建直到毁灭的整个过程。以下是 Servlet 遵循的过程：
>
> - Servlet 通过调用 **init ()** 方法进行初始化。
> - Servlet 调用 **service()** 方法来处理客户端的请求。
> - Servlet 通过调用 **destroy()** 方法终止（结束）。
> - 最后，Servlet 是由 JVM 的垃圾回收器进行垃圾回收的。



### init()方法



未完待续...