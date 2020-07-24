## 一、个人博客的搭建过程
### 1、常见个人博客搭建方案

搭建个人博客一般有三种方式：

- WorkPress：一般需要独立域名（收费），对 MarkDown 不友好
- GitHubPages + Jekell：免费，稍微有点麻烦
- GitHubPages + Hexo：免费，使用简单，使用者众多*（我们接下来要介绍的博客的搭建就是基于这种方式。）*




### 2、Hexo简介 

*Hexo 是一个基于 Nodejs 的静态博客网站生成器，作者是来自台湾的 [Tommy Chen](https://zespia.tw/)*

[Hexo官网：https://hexo.io/](https://hexo.io/)



特点：

- 不可思议的快速 ─ 只要一眨眼静态文件即生成完成
- 支持 Markdown
- 仅需一道指令即可部署到 GitHub Pages 和 Heroku
- 已移植 Octopress 插件
- 高扩展性、自订性
- 兼容于 Windows, Mac & Linux





### 3. 博客搭建正式开始

（1）创建一个github仓库：Create a new repository.

（2）注意 Respository name 中一定要输入：你的用户名.github.io。其他地方不用修改，然后直接点 ”Create repository“ 按钮完成创建即可。

![1](https://user-images.githubusercontent.com/23518990/68289023-649db780-00c0-11ea-8b23-d4e42b56343e.jpg)


（3）本地环境搭建：

- 安装[Git](https://git-scm.com/download/)，步骤省略。
- 安装[Nodejs](https://nodejs.org/en/download/)，步骤省略。
- 安装[Hexo](https://hexo.io/)，打开官网：
  
![2](https://user-images.githubusercontent.com/23518990/68289040-69fb0200-00c0-11ea-8183-3e49f8558be3.jpg)


是不是很简洁，只有一条指令！而且我们只需要使用windows的cmd就可以下载安装。

打开cmd，输入指令：

```
npm install hexo-cli -g
```

Hexo安装完成，是不是超简单^_^





### 4、 创建本地博客

在cmd里面定位到你想保存博客的文件夹*（我的位于 G:/Blog/ 目录下）*

用cmd定位到这个文件夹下：

![3](https://user-images.githubusercontent.com/23518990/68289053-6ebfb600-00c0-11ea-87d2-79f8039baf65.jpg)


之后，使用以下指令创建本地博客：

```
hexo init 你的用户名.github.io  // 建议和创建仓库时使用同一个，我的是Daotin.github.io
```


### 5、 Next主题的安装

经过上面步骤创建完本地博客之后，基本的博客系统就已经搭建好了，自带了 landscape 主题。不过该主题不是很符合我的审美，在网上搜索了一下 Hexo 主题，选择了用户量较大的 Next。

Next 是 iissnan 在 GitHub 上开源的一个 Hexo 主题，主打简洁，但是功能齐全，使用者众多。

> ”说明：“在 Hexo 中有两份主要的配置文件，其名称都是 _config.yml。 其中，一份位于站点根目录下（即 xxx.github.io 目录下），主要包含 Hexo 本身的配置；另一份位于主题目录下，这份配置有主题作者提供，主要用于配置主题相关的选项。为了描述方便，在以下说明中，将前者称为 “站点配置文件”， 后者称为 “主题配置文件”。


看下怎么安装Next主题：

cmd 下切换到本地 Daotin.github.io 目录下，之后输入如下指令：

```
git clone https://github.com/iissnan/hexo-theme-next themes/next
```

之后我们就可以在 Daotin.github.io\themes\ 下看到 next 主题文件夹：

![4](https://user-images.githubusercontent.com/23518990/68289067-7717f100-00c0-11ea-93b0-4c63fee69ed3.jpg)



### 6、使用Next主题

首先，复制一份打开本地博客目录下的 **_config.yml** 文件，命名为 _config.yml.bak，做为备份，以防改错。然后，使用文本编辑器打开本地博客目录下的 _config.yml 文件，搜索，定位 theme 键值，将原本的 theme 的值注释掉，新建一个新的 theme 值为 next.

```
theme: next
```

> 注意：该配置文件中的键值之间一定要有空格，否则轻则没有作用，重则报错，无法启动。





### 7、 站点配置文件基本项修改

这里先看看最基础的配置，也就是必须要改动的：


```
title: xxx  # 博客的名字，也称站点名称
author: xxx # 作者名字
description: xxx # 对站点的描述，搜索引擎会抓取，可以自定义（这个还是加上比较好）
language: zh-Hans # 语言 简体中文
theme: next  # 配置主题
deploy: # 部署相关配置
    type: git # 使用 Git 提交
    repo: https://github.com/Daotin/Daotin.github.io.git # 就是存放博客的仓库地址
```

> 上述配置是必须要修改的，再次强调，键值之间一定要 ”加空格“，请在文本编辑器中搜索定位后再修改。


**站点配置文件详细配置示例**


```
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site 这里的配置，哪项配置反映在哪里，可以参考我的博客
title: xxx # 博客的名字，也称站点名称
subtitle: xxx # 副标题
description: xxx # 对站点的描述，搜索引擎会抓取，可以自定义
author: xxx # 作者名字
language: zh-Hans # 语言 简体中文
timezone:  # 用默认的即可

# URL 
# 这项暂时不需要配置，绑定域名后，要创建 sitemap.xml 时再配置该项
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: # http://xxx.com
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory
# 目录，不要修改
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing 
# 文章布局、写作格式的定义，不修改
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Date / Time format 
# 日期 / 时间 格式，不要修改
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: MMM D YYYY
time_format: H:mm:ss

# Pagination 
# 每页显示文章数，可以自定义
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Extensions 
# 配置站点所用主题和插件，这里将默认主题注释，修改为 next
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next
#theme: landscape

# 头像
# 注意：是 xxx.github.io/source 下的开始的相对路径，如果 source 文件夹下面没有 uploads 文件夹，那么新建一个。考虑到会博客中用很多图片，在 uploads 文件夹下请分好类，避免混乱
avatar: /uploads/../img/avatar.jpg

# Deployment 
# 本地博客部署到 github 上要配置这里
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git # 使用 Git 提交
  repository: https://github.com/xxx/xxx.github.io.git # 就是存放博客的仓库地址
```


下面是我自己的文件详细配置：**Daotin.github.io/_config.yml文件**

```

# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: Daotin's Home
subtitle: 说好的幸福呢
description: 每天进步一点点
author: Daotin
language: zh-Hans
timezone:

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yoursite.com
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:
  
# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date
  
# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next
#theme: landscape

# 头像
# 注意：是 xxx.github.io/source 下的开始的相对路径，如果 source 文件夹下面没有 uploads 文件夹，那么新建一个。考虑到会博客中用很多图片，在 uploads 文件夹下请分好类，避免混乱
avatar: /uploads/touxiang/touxiang.jpg

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: https://github.com/Daotin/Daotin.github.io.git
```


以上基本本地博客就已经搭建好了，我们可以先看看效果：

在 cmd 下定位到 xxx.github.io 目录，输入命令：

```
$ hexo s // hexo server
```

启动成功可以看到提示，按照提示用浏览器打开提示网址 **http://localhost:4000/** ，即可看到你的本地博客了，里面有一篇系统自带的 Hello World 文章.

![5](https://user-images.githubusercontent.com/23518990/68289099-84cd7680-00c0-11ea-9181-c1f50d4fb7b1.jpg)



### 8、 Next 配置

当然，最权威的是看[官方的说明文档](http://theme-next.iissnan.com/getting-started.html#theme-settings)，我在这里提供一个示例，供大家参考，你可以直接拷过去稍微改动一点就行。

**Next 配置就是上面所说的”主题配置文件“，位于 xxx.github.io/themes/next 目录下，文件名为 _config.yml。老规矩，先备份一份  ”_config.yml.bak“，以防改错。**


以我的博客为例，阐述一下需要配置的地方：


```
# Set default keywords (Use a comma to separate)
# 设置关键字
keywords: "Android, DIY"

# Specify the date when the site was setup
# 设置博客开始时间
since: 2017

# When running the site in a subdirectory (e.g. domain.tld/blog), remove the leading slash (/archives -> archives)
# 设置菜单，就是[我的博客](http://Daotin.github.io)左侧那一列
menu: 
  #home: /
  home: / || home
  archives: /archives/ || archive
  #archives: /archives
  categories: /categories/ || th
  #categories: /categories
  tags: /tags/ || tags
  #tags: /tags
  about: /about/ || user
  #about: /about
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat

# Schemes
# 设置风格
#scheme: Muse
#scheme: Mist
scheme: Pisces # 我的就是这个双栏风格

# Automatically Excerpt. Not recommand.
# Please use <!-- more --> in the post to control excerpt accurately.
auto_excerpt:
  enable: true # 设置是否显示阅读全文，文章较多的话，有必要设置为 true
  length: 150

# 一些第三方服务设置，这里只提一下”多说“，其他的请参考官方介绍
# Make duoshuo show UA
# user_id must NOT be null when admin_enable is true!
# you can visit http://dev.duoshuo.com get duoshuo user id.
duoshuo_info:
  ua_enable: true
  admin_enable: true
  user_id: 0 # **这里不要动，千万别动**
  admin_nickname: DIY-green

# Code Highlight theme
# Available value:
#    normal | night | night eighties | night blue | night bright
# https://github.com/chriskempson/tomorrow-theme
#highlight_theme: normal
# 代码高亮主题
highlight_theme: night eighties

# 打赏配置
# 打赏说明文本
reward_comment: 坚持原创技术分享，您的支持将鼓励我继续创作！
# 微信收款二维码
wechatpay: /uploads/pay/wechatpay.jpg
# 支付宝收款二维码
alipay: /uploads/pay/alipay.jpg

# 订阅微信公众号
# Wechat Subscriber
#wechat_subscriber:
#  enabled: true
#  qcode: /uploads/wechat-qcode.jpg
#  description: 欢迎您扫一扫上面的微信公众号，订阅我的博客！

```


> **（PS：在设置菜单这一项，就是我的博客左侧那一列就使用默认的设置就可以了，之前改成了注释的部分，导致菜单栏的图标都变成了问号，谢谢帅张星球的“少年”提醒经过改正，以上。）**



### 9. 创建分类页面

（1）打开命令行，定位到 Daotin.github.io 目录；
（2）新建一个页面，命名为 categories；
```
hexo new page categories
```

（3）根据提示找到新建的 index.md 文件，编辑；

```
---

title: 分类
date: 2017-10-30 20:45:01
type: "categories" # 将页面的类型设置为 categories，主题将自动为这个页面显示所有分类
comments: false    # 如果有启用多说 或者 Disqus 评论，默认页面也会带有评论。需要关闭的话，设置为 false

---
```


### 10. 创建标签云页面

如下图：

![6](https://user-images.githubusercontent.com/23518990/68289128-91ea6580-00c0-11ea-9504-59f90870688a.jpg)




（1）打开命令行，定位到 Daotin.github.io 目录；
（2）新建一个页面，命名为 tags；

```
hexo new page tags
```

（3）根据提示找到新建的 index.md 文件，编辑；

```
---

title: All tags 
date: 2016-04-27 08:56:40
type: "tags"    # 将页面的类型设置为 tags，主题将自动为这个页面显示标签云
comments: false # 如果有启用多说 或者 Disqus 评论，默认页面也会带有评论。需要关闭的话，设置为 false

---
```


> 注意事项
>
> - 格式再次强调，设置项的键值之间一定要有空格；
> - 菜单上显示 ”分类“ 等栏目。如果需要在菜单上显示 ”分类“ 和 ”标签“ 等，那么记得打开注释，或者添加该条目；
> - 关于第三方服务的 ”duoshuo_info“。在配置该项的时候，user_id 键对应的值不要修改，也就是保持为 0，具体原因我不清楚，如果修改了该值，那么你的博客会变得一片空白；
> - 分类和标签云页面。首先，要使用” hexo new page “命令生成这两个页面，否则报404。其次，这两个页面是主题自动维护的，只要我们的文章按照规矩来就行了，下面会详细说明。







## 二. 写博客与发布

经过上述步骤，本地博客和主题设置已经完成，那么接下来就是写博客了。

你的博客文件需要存放到 **Daotin.github.io/source/_posts 文件夹**中，在该文件夹下面你可以按照你的博客分类建立一系列的文件夹来管理博客原文件。

操作步骤：



### 1、用 Markdown 写文章

不管你用什么编辑 Markdown 文件，最后生成的 md 文件放到 Daotin.github.io/source/_posts 文件夹或其子文件夹中即可，如：

或者使用指令：

```
hexo new "xxx"  // xxx 为Markdown文件名，如 xxx.md
```

/source/_posts文件夹内除了xxx.md文件还有一个同名的文件夹，以后我们xxx博文需要插入的图片就放到对应的同名文件夹下，方便添加图片与归类。

md文章的内容格式如下：

```
---

title: 个人博客搭建详解   # 这是标题
categories:            # 这里写的分类会自动汇集到 categories 页面上，分类可以多级
- 实用技术               # 一级分类
- 个人博客               # 二级分类 
tags:                 # 这里写的标签会自动汇集到 tags 页面上
- 实用               # 可配置多个标签，注意格式
- 个人博客

#  下面写正文部分。。。

---
```

> 注意：分类和标签是自动维护的，关键是的文章要按照规定的格式写，如上格式，可以参考。
> 说明：Next 主题会自动生成目录，这也省了不少事。



### 2、本地运行测试

打开命令行定位到 xxx.github.io 目录，输入命令：

```
hexo s // hexo server  启动服务预览
```



### 3、在浏览器查看效果
在浏览器中输入 **http://localhost:4000** 访问本地博客，看看效果吧。



### 4、安装自动部署发布工具
这里用到了 **hexo-deployer-git**，使用如下命令安装：

```
npm install hexo-deployer-git --save
```



### 5、发布到 GitHub Pages 
确认在本地上显示无误之后，就可以将 md 转为 静态网页文件，然后发布到 GitHub Pages 上去了。

```
hexo clean #清除缓存 网页正常情况下可以忽略此条命令
hexo g     #生成静态网页
hexo d     #开始部署

也可以一次性执行
hexo clean && hexo g && hexo d
```

如果是第一次部署，终端会提示要求输入用户名和密码。等命令执行完之后，过几分钟打开 http://Daotin.github.io 即可看到你的个人博客了。以后要发布新文章，执行上述命令即可。



> 注意事项
> - Git 的 bug
>   有个老版本的 Git 有个 bug，上传的时候会提示非法域名这类的，要解决该问题，最简单的方法就是更新 Git，用最新版的 Git；
>
> - 关于页面空白
>   主题配置文件中的 ”duoshuo_info“ 下的 ”user_id“ 如果是非 ”0“，会导致该问题
>
> - 特殊字符导致报错
>   如添加新博客的时候报错了，而且提示的是 js 中某些地方报错，那么很可能是 md 文件中存在特殊字符（不是正常显示的字符，不是说特殊符号，能正常显示的都不是这里说的特殊字符），把特殊字符删除即可
>
> - **使用hexo，如果换了电脑怎么更新博客？**
>   这个问题相信大家都关心，知乎上有比较详细的解答。我说一下我的解决方法吧！
>   ​
>   在新电脑上配置好本地博客环境，然后，直接拷贝原电脑上的 xxx.github.io 文件夹到新电脑上即可。
>   将 xxx.github.io 文件夹同步到网上(如：Dropbox 等)，其他任何电脑（配置好了本地博客环境）要用的时候，从网上同步下来即可。



## 三、参考资料

[免费个人博客搭建详解](http://www.jianshu.com/p/380290deb8f0)



