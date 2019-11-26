---
title: 如何在hexo中使用LaTeX数学公式
date: 2019-07-16 18:55:34
tags:
    - hexo
    - LaTeX
categories:
    - 技术
author: Tern
authorLink: www.cputern.top
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
avatar: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/icon/favicon.png
comments: true
keywords: hexoLaTeX
description: hexo中使用LaTeX数学公式
photos: https://cdn.jsdelivr.net/gh/TernYoung/nicePicture/smallPic/pic007.jpg
---


### hexo的数学公式问题

在 `hexo` ，竟然不能用 `LaTeX` 写数学公式，对于写需要数学公式的文章非常不方便，这里我们来解决这个问题。



---

#### 第一步：用Kramed代替Marked

我们需要用 `mathjax` 来解决这个问题，但是`hexo` 的默认渲染引擎是 `marked` ， `marked ` 不支持 `mathjax` ,所以我们要用 `kramed` , `kramed`是在 `marked`的基础上进行修改。我们在工程目录下执行命令安装 `kramed`。

```bash
npm uninstall hexo-renderer-marked --save
npm install hexo-renderer-kramed --save
```

然后，找到/node_modules/hexo-renderer-kramed/lib/renderer.js，

更改：

```javascript
// Change inline math rule
function formatText(text) {
    // Fit kramed's rule: $$ + \1 + $$
    return text.replace(/`\$(.*?)\$`/g, '$$$$$1$$$$');
}
```

为：

```javascript
// Change inline math rule
function formatText(text) {
    return text;
}
```



---


#### 第二步：停止使用hexo-math

卸载 `hexo-math` :

```bash
npm uninstall hexo-math --save
```

然后安装 `hexo-renderer-mathjax` :

```bash
npm install hexo-renderer-mathjax --save
```



---

#### 第三步：更新 Mathjax 的 CDN 链接

打开/node_modules/hexo-renderer-mathjax/mathjax.html

把 `script`改为：

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"></script>

```



---

#### 第四步：更改默认转义规则

因为 `hexo` 的转义规则和`markdown`转义规则有冲突，稍作修改

打开node_modules\kramed\lib\rules\inline.js，

找到第11行的`escape`变量:

```javascript
escape: /^\\([\\`*{}\[\]()#$+\-.!_>])/,
```

改为：

```javascript
escape: /^\\([`*\[\]()# +\-.!_>])/,
```

同时把第20行的em变量:

```javascript
em: /^\b_((?:__|[\s\S])+?)_\b|^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,
```

改为：

```javascript
em: /^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,
```



---

#### 第五步：开启mathjax

在主题 `_config.yml` 中开启 `mathjax`， 找到 `mathjax` 字段添加如下代码：

```yml
mathjax:
    enable: true
```

没有找到的话直接添加在末尾。

在需要用到数学公式的文章开启 `mathjx`

```markdown
---
title: Testing Mathjax with Hexo
category: Uncategorized
date: 2017/05/03
mathjax: true
---
```

完成以上步骤即可用 `hexo` 写 `LaTeX` 数学公式