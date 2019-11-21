---
title: Hexo搭建个人博客
date: 2019-11-20 18:38:45
categories: 
    - hexo
    - 博客
tags: 
    - hexo
    - github
---


# Hexo 搭建博客

> Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 [Markdown](http://daringfireball.net/projects/markdown/)（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。依赖少易于安装使用，可以方便的生成静态网页托管在GitHub和Coding上，是搭建博客的首选框架。

> [ Hexo官网](https://hexo.io/zh-cn/docs/) 因为Hexo的创建者是台湾人，对中文的支持很友好，可以选择中文进行查看。

## 第一部分：Hexo搭建步骤

### Hexo的初级搭建还有部署到github page上，以及个人域名的绑定。

####　1. 安装Git

Windows: [Download git](https://gitforwindows.org/) ,下载后有个Git Bash命令行工具，用这个工具来使用git

Linux: 输入命令`sudo apt-get install git`，安装好后，用`git --version` 查看版本



####　2. 安装Node.js

Windows：[Download Node.js](https://nodejs.org/en/download/) 选择LTS版本

Linux：输入以下命令安装

```linux
sudo apt-get install nodejs
sudo apt-get install npm
```

安装完毕后，打开命令行,输入以下命令，检查安装是否成功

```linux
node -v
npm -v
```

> Tips：Windows 安装 git 后可以用 git bash 敲命令行



####　3. 安装Hexo

先创建一个文件夹Blog，然后cd到这个文件夹下

输入命令：

```linux
npm install -g hexo-cli
```

用 `hexo - v` 查看下版本

安装完毕

初始化 hexo , myblog 为你想取的名

```linux
hexo init myblog
cd myblog
npm install
```

建完成后，指定文件夹目录下有：

- node_modules: 依赖包
- public：存放生成的页面
- scaffolds：生成文章的一些模板
- source：用来存放你的文章
- themes：主题
- _config.yml: 博客的配置文件

部署hexo服务，在浏览器输入localhost:4000就可以看到你生成的博客了。

```linux
hexo g
hexo server
```

使用Ctrl + C 关闭服务

####　4. Github创建个人仓库

登录 Github 账户，没有的注册一个。

登录后，点击New repository，新建仓库

> 创建一个和你用户名相同的仓库，[后面加.github.io](http://xn--yfr16an19l.github.io)，只有这样，将来要部署到GitHub page的时候，才会被识别，[也就是xxxx.github.io](http://xn--xxxx-4m5f354ev5p.github.io)，其中xxx就是你注册GitHub的用户名。我这里是已经建过了。

点击 Create repository。



####　5. 生成SSH添加到Github

回到git bash中，输入：

```git
git config --global user.name "yourname"
git config --global user.email "youremail"
```

yourname是你的GitHub用户名，youremail是你GitHub的邮箱。

可以输入以下命令检查输入是否正确：

```git
git config --list
```

然后创建SSH，一路回车

```git
ssh-keygen -t rsa -C "youremail"
```

这个时候它会告诉你已经生成了.ssh的文件夹。在你的电脑中找到这个文件夹。

> SSH是一个秘钥，id_rsa是这台电脑的私人秘钥，id_ras.pub是公开秘钥。把公钥放在Github上，当你链接GitHub自己的账户时，它就会根据公钥匹配你的私钥，当能够相互匹配时，才能够顺利的通过git上传你的文件到GitHub上。

在GitHub的setting中，找到SSH keys设置选项，点击`New SSH key` 把`id_rsa.pub`里的信息复制过去。

最后在gitbash中查看是否成功

```git
ssh -T git@github.com
```



####　6. 将hexo部署到GitHub

hexo与GitHub关联，将hexo生成的文章部署到GitHub上，打开站点配置文件`_config.yml`,翻到最后，修改为YourGitHubName，也就是你的GitHub账户

```json
deploy:
  type: git
  repo: https://github.com/YourgithubName/YourgithubName.github.io.git
  branch: master
```

这个时候需要先安装deploy-git，这样才能用命令部署到GitHub。

```linux
npm install hexo-deployer-git --save
```

然后

``` linux
hexo clean
hexo generate
hexo deploy
```

`hexo clean`清除了你之前生成的东西，也可以不加。
`hexo generate` 顾名思义，生成静态文章，可以用 `hexo g`缩写
`hexo deploy` 部署文章，可以用`hexo d`缩写

> Tips: deploy时可能要你输入username和password。

部署成功的话，可以在`http://yourname.github.io` 看到你的博客



####　7. 设置个人域名

现在个人网站的地址是 `yourname.github.io` ,如果觉得这个网址的逼格不够，那就要购买设置自己的个人域名。这里介绍在 [阿里云](https://wanwang.aliyun.com/?spm=5176.8142029.digitalization.2.e9396d3e46JCc5) 上购买域名，各个后缀的价格不一样，.com比较贵，其它的有的很便宜。

你需要先去进行实名认证,然后在域名控制台中，看到你购买的域名。点**解析**进去，添加解析。

| 主机记录 | 记录类型 | 解析线路（isp） | 记录值             | TTL    |
| -------- | -------- | --------------- | ------------------ | ------ |
| www      | CNAME    | 默认            | yourname.github.io | 10分钟 |

登录GitHub，进入之前创建的仓库，点击settings，设置Custom domain，输入你的域名

然后在博客文件source种创建一个名为CNAME文件，不要后缀，写上你的域名。

最后在gitbash中输入

```git
hexo clean
hexo g
hexo d
```

打开浏览器，输入你自己的域名，就可以看见你的博客了。



#### 8. 发布文章

这样你就可以开始写文章了

```linux
hexo new newpapername
```

> Tips: 可以直接在source/_post 中创建.md文件，然后直接编辑也可。

然后再source/_post 中打开.md文件，就可以开始编辑了。当写完三连

```linux
hexo clean
hexo g
hexo d
```

即可在网站上看到更新。



## 第二部分： Hexo配置

### Hexo的基本配置，更换主题，实现多终端工作，以及再coding page部署实现国内外分流。

#### 1. Hexo基本配置

博客文件根目录下的 `_config.yml` ,是整个Hexo框架的配置文件。里面有大部分配置。详细可参考 [官方配置文档](https://hexo.io/zh-cn/docs/configuration)

``` yml
theme: landscape

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: <repository url>
  branch: [branch]


```

`theme`就是选择什么主题，也就是在`theme`这个文件夹下，在官网上有很多个主题，默认给你安装的是`lanscape`这个主题。当你需要更换主题时，在官网上下载，把主题的文件放在`theme`文件夹下，再修改这个参数就可以了。

接下来这个`deploy`就是网站的部署的，`repo`就是仓库(Repository)的简写。`branch`选择仓库的哪个分支。这个在之前进行github page部署的时候已经修改过了，不再赘述。而这个在后面进行双平台部署的时候会再次用到。

##### Front-matter

Front-matter 是文件最上方以 `--- ` 分隔的区域，用于指定个别文件的变量，举例来说：

    title: Hello World
    date: 2013/7/13 20:46:25
    ---

下是预先定义的参数，您可在模板中使用这些参数值并加以利用。

|     参数     |         描述         |
| :----------: | :------------------: |
|   `layout`   |         布局         |
|   `title`    |         标题         |
|    `date`    |       建立日期       |
|  `updated`   |       更新日期       |
|  `comments`  |  开启文章的评论功能  |
|    `tags`    | 标签（不适用于分页） |
| `categories` | 分类（不适用于分页） |
| `permalink`  |     覆盖文章网址     |

其中，分类和标签需要区别一下，分类具有顺序性和层次性，也就是说 `Foo, Bar` 不等于 `Bar, Foo`；而标签没有顺序和层次。

```markdown
categories:
    - Diary
tags:
    - PS3
    - Games
```

#### 2. 更换主题

如果觉得默认的 `landscape` 主题不好看，那么可以在官网的主题中，选择你喜欢的一个主题[官网主题](https://hexo.io/themes/) 

直接在github链接上下载下来，然后放到 `theme` 文件夹下就行了，然后再在刚才说的配置文件中把 `theme` 换成那个主题文件夹的名字，它就会自动在 `theme` 文件夹中搜索你配置的主题。

而后进入 `hueman` 这个文件夹，可以看到里面也有一个配置文件 `_config.xml`，貌似它默认是 `_config.xml.example` ，把它复制一份，重命名为 `_config.xml` 就可以了。这个配置文件是修改你整个主题的配置文件。



#### 3.git分支进行多终端工作

> 如果有两台电脑就会碰见这个问题，你现在在自己的笔记本上写的博客，部署再了网站上，那么你在家里用台式机，或者实验室的台式机，发现你电脑里面没有博客的文件，或者要换电脑了，最后不知道怎么移动文件，怎么办？在这里我们就可以利用git的分支系统进行多终端工作了，这样每次打开不一样的电脑，只需要进行简单的配置和在github上把文件同步下来，就可以无缝操作了。

**机制**

> `hexo d` 部署到 GitHub 上的其实是 hexo 编译后的文件，是用来生成网页的，不包含源文件。去 GitHub 上查看，并没有 source 等源文件在上面，也就是上传的是在本地目录里自动生成的`.deploy_git`里面。其他文件 ，包括我们写在 source 里面的，和配置文件，主题文件，都没有上传到 GitHub.

可以利用 git ，将源文件上传到 GitHub 的另一个分支。

**上传分支**

> 在 GitHub 中的博客仓库新建一个 hexo 分支，然后在这个仓库的 settings 中，选择默认分支为 hexo分支（这样每次同步的时候就不用指定分支，更方便）。

然后在想要保存的目录下，输入以下命令：

```linux
git clone git@github.com:YourGitHubName/YourGitHubName.github.io.git
```

将其克隆到本地，因为默认分支已经设成了hexo，所以clone时只clone了hexo。

接下来在克隆到本地的`YourGitHubName.github.io`中，把除了.git 文件夹外的所有文件都删掉，把之前我们写的博客源文件全部复制过来，除了`.deploy_git`。这里应该说一句，复制过来的源文件应该有一个`.gitignore`，用来忽略一些不需要的文件，如果g没有的话，自己新建一个，在里面写上如下，表示这些类型文件不需要git：

```gitignore
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```

> 注意，如果你之前克隆过theme中的主题文件，那么应该把主题文件中的`.git`文件夹删掉，因为git不能嵌套上传，最好是显示隐藏文件，检查一下有没有，否则上传的时候会出错，导致你的主题文件无法上传，这样你的配置在别的电脑上就用不了了。

然后：

```git
git add .
git commit –m "add branch"
git push 
```

这样就上传完了，可以去你的github上看一看hexo分支有没有上传上去，其中`node_modules`、`public`、`db.json`已经被忽略掉了，没有关系，不需要上传的，因为在别的电脑上需要重新输入命令安装 。

**更换电脑后**

跟前面搭建环境一样：

* 安装git

```linux
sudo apt-get install git
```

* 设置git全局邮箱和用户名

```git
git config --global user.name "yourgithubname"
git config --global user.email "yourgithubemail"
```

* 设置ssh key

```git
ssh-keygen -t rsa -C "youremail"
#生成后填到github和coding上（有coding平台的话）
#验证是否成功
ssh -T git@github.com
ssh -T git@git.coding.net #(有coding平台的话)
```

* 安装node.js

```linux
sudo apt-get install node.js
sudo apt-get install npm
```

* 安装hexo

```linux
sudo npm install hexo-cli -g
```

* 获取博客源码

```linux
git clone git@………………
```

* 进入文件夹

```linux
cd xxx.github.io
npm install
npm install hexo-deployer-git --save
```

* 生成网页，部署

```linux
hexo g
hexo d
```

然后就可以写新的博客了

记得每次写完都把源文件上传一下

```git
git add .
git commit –m "xxxx"
git push 
```

如果是在已经编辑过的电脑上，已经有clone文件夹了，那么，每次只要和远端同步一下就行了

```git
git pull
```

#### 4.coding page 上部署实现国内外分流

> 之前我们已经把hexo托管在github了，但是github是国外的，而且百度的爬虫是不能够爬取github的，所以如果你希望你做的博客能够在百度引擎上被收录，而且想要更快的访问，那么可以在国内的coding page做一个托管，这样在国内访问就是coding page，国外就走github page。

1. 申请 coding 账户，新建项目

   先申请一个账户，然后创建新的项目，这一步项目名称应该是随意的。

2. 添加ssh key

   这步跟github一样

   添加完后，检查一下是否添加成功

   ```git
   ssh -T git@git.coding.net
   ```

3. 修改 _config.yml

   hexo官方文档是这样的：

   ```yml
   deploy:
     type: git
     message: [message]
     repo:
       github: <repository url>,[branch]
       coding: <repository url>,[branch] 
   ```

   我们只需要：

   ```yml
   deploy:
     type: git
     repo: 
       coding: git@git.coding.net:ZJUFangzh/ZJUFangzh.git,master
       github: git@github.com:ZJUFangzh/ZJUFangzh.github.io.git,master
   ```

4. 部署

   保存一下，直接

   ```linux
   hexo g
   hexo d
   ```

   这样就可以再coding的项目上看到你的部署的文件了

5. 开心coding pages服务，绑定域名

6. 阿里云添加解析

7. 去除coding page的跳转广告

   coding page的一个比较恶心人的地方就是，你只是银牌会员的话，访问会先跳转到一个广告，再到你自己的域名。那么它也给出了消除的办法。右上角切换到coding的旧版界面，默认新版是不行的。然后再来到`pages服务`这里。

   只要你在页面上添加一行文字，写`Hosted by Coding Pages`，然后点下面的小勾勾，两个工作日内它就会审核通过了。

   ```html
   <p>Hosted by <a href="https://pages.coding.me" style="font-weight: bold">Coding Pages</a></p>
   ```

   我的选择是把这一行代码放在主题文件夹`/layout/common/footer.ejs`里面，也就是本来在页面中看到的页脚部分。

   当然，为了统一，我又在后面加上了and **Github**哈哈，可以不加。

   ```html
   <p><span>Hosted by <a href="https://pages.coding.me" style="font-weight: bold">Coding Pages</a></span> and <span><a href="https://github.com" style="font-weight: bold">Github</a></span></p>
   ```



## 第三部分

### hexo添加各种功能，包括搜索的SEO，阅读量统计，访问量统计和评论系统等。请转 [visugar](http://visugar.com/2017/08/01/20170801HexoPlugins/) 