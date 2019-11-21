---
title: hexo添加百度统计和Livere(来必应)评论插件
date: 2019-07-17 16:53:20
tags:
    - hexo
    - 百度统计
    - Livere
categories:
    - 博客配置
cover: static/images/hexolivere/cover.png
mp3: http://link.hhtjim.com/163/5146554.mp3
---

## `Hexo` 添加 `百度统计`

本方法在`diaspora`主题配置成功

#### 第一步：注册并登录 [百度统计](https://tongji.baidu.com/web/welcome/login) 获取统计代码

#### 第二步：修改主题下的`_config.yml`

添加代码：

```yml
baidu_tongji:
  enable: true
  sitecode:  69edb2848756110a4dbea314xxxx ##代码中js?后的一串英文与数字代码
```

#### 第三步：复制统计代码到`head.ejs`文件中

找到 `themes\diaspora\layout\partial\head.ejs` 文件,把刚才获取的统计代码复制到 `</head>` 之前

#### 第四步：部属三连

```bash
hexo clean
hexo g
hexo d
```

#### 第五步：返回百度统计页面，进行代码安装检测，此时应该检测成功，然后就能看到百度统计报告了

---

## `Hexo`添加 `Livere评论`插件

本方法在`diaspora`主题配置成功

之前有 `gittalk`，但是只能用 `github` 登录，感觉不是很方便，听说 `Valine`很好用，但是注册还要实名认证，手持身份证照片，感觉有点傻，不是很必要，然后发现 `Livere` 很好，支持各种帐号登录，不用实名认证，

#### 第一步：去 [Livere官网](https://livere.com/) 注册选择免费版获取 `安装代码`

#### 第二步：修改主题下的 `_config.yml` 

添加代码：

```yml
#livere评论系统
	livere:
	livere_uid: 这里填安装代码中的data-uid
```

#### 第三步：在主题目录下需要评论地方加入安装代码

我需要在每篇文章结束的地方加入评论模块，所以需要在文章详情页面`post.ejs` 里添加 `安装代码`于是就在`themes\diaspora\layout\_partial`共用模块文件夹 `_partial` 下 新建 `livere.ejs` 并把安装代码 放在里面 ，然后在 `post.ejs` 中对应位置 `partial('_partial/livere')` 引用即可

#### 第四步：部属三连

```
hexo clear
hexo g
hexo d
```

#### 第五步：看文章底下的Livere评论，若没有则刷新试试

