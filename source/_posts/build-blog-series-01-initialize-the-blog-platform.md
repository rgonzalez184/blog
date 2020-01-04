---
title: 搭建博客系列01-初始化博客平台
date: 2020-01-04 00:40:42
tags: 实战
categories: 搭建博客系列
---

快速初始化博客平台,生产内容为主
<!-- more -->

## 1 为什么要写博客

我准备在2020年开始之初, 让自己的博客回归.为了培养自己表达能力、坚持不懈能力.不想轻易放弃一个决定,一个事情.所以准备坚持写属于自己的技术博客,如果对你有用你也可以阅读一下,没用就立马关掉.切记不要浪费自己的时间,因为时间真的很珍贵的.还有一点,就是自己要重新带一个新团队,起个带头作用.希望团队成员都可以坚持总结自己技术博客.

## 2 博客平台选择

我选择的博客平台,主要是自建博客平台Hexo.然后多分发、多备份的形式.

分发平台:

* 稀土掘金
* SF
* Medium
* 方格子
* 简书

备份平台:

* CSDN
* 博客园
* Blogger
* DEV Community

笔记平台:

* 印象笔记
* Notion

## 3 初始化博客平台

{% note info %}
### 我的系统环境
* 操作系统:
{% endnote %}

### 3.1 本地初始化Hexo平台

* 中国大陆的正常上网解决方案

{% note danger %}
说明Tips:
我所在的新疆地区,限制比较严格.使用GitHub也有问题
下面是我的解决方案,原理性的知识不多解释.这是实战分类
{% endnote %}

需要先购买VPS自行搭建正常上网服务或购买别人已经搭建好的服务,我选择的第二个种

我使用的是: [海豚湾](https://海豚湾.com/),我是和一个同学合买的.选择大海豚的季度套餐

购买之后,获取订阅地址

设置本地客户端-ShadowsocksR(版本:ShadowsocksR-win-4.9.0)

解压ShadowsocksR-win-4.9.0.zip的压缩包, 打开ShadowsocksR-dotnet4.0.exe

下面就看到小飞机的图标,右键选择:服务器订阅-SSR服务器订阅设置

点击Add,在网址中填入订阅地址,勾选自动更新,点击确定

选择:系统代理模式-直连模式

选择:服务器订阅-更新SSR服务器订阅(不通过代理),出现更新成功的提示,我们就添加好需要使用的服务器

选择:代理规则-绕过局域网和大陆

选择:服务器-海豚湾-选择比较快的服务器(自己根据当时的网络情况测试)

选择:系统代理模式-全局模式

开启了正常上网,这时候我们大部分程序都可以正常上网,但是终端模拟器(Powershell、Bash)无法正常上网,要使用下面的代理工具

设置代理工具-Proxifier(版本:Proxifier Standard Edition v3.42)

{% note danger %}
### 学习使用
Your name or company name: Ronny Gonzalez
Your registration key: 5EZ8G-C3WL5-B56YG-SCXM9-6QZAP
{% endnote %}

设置01-Proxy Servers:

点击Add
Server
Address:127.0.0.1 Port:1080
Protocol
SOCKS Version 5
点击Check
点击OK,之后一路点击OK

设置02-Proxification Rules:

点击Add
Name:SSR
Applications: 点击Browse,找到shadowsocksr-dotnet4.0.exe，点击打开
Action:Direct
点击OK，点击OK

设置03-Name Resolution:
先取消勾选 Detect DNS settings automatically
勾选Resolve hostname through proxy

{% note danger %}
Tips:
接下来所有操作都在正常上网环境下
{% endnote %}

* 安装和设置包管理工具-Scoop

选择Scoop是因为可以自定义安装路径

权限问题解决方案:

在 Windows Powershell 上右键-以管理员身份运行

```shell
# 解决权限问题
PS C:\Windows\system32> Set-ExecutionPolicy RemoteSigned -scope CurrentUser
接下来输入 A
```

自定义安装路径安装Scoop

```shell
# C:\Apps\Scoop 替换成你自己的
PS C:\Windows\system32> [environment]::setEnvironmentVariable('SCOOP','C:\Apps\Scoop','User')
PS C:\Windows\system32> $env:SCOOP='C:\Apps\Scoop'
PS C:\Windows\system32> Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
```

自定义Scoop安装软件的路径

```shell
# C:\Apps\ScoopApps 替换成你自己的
PS C:\Windows\system32> [environment]::setEnvironmentVariable('SCOOP_GLOBAL','C:\Apps\ScoopApps','Machine')
PS C:\Windows\system32> $env:SCOOP_GLOBAL='C:\Apps\ScoopApps'
```

增加bucket,用于安装带GUI的软件

{% note info %}
### Tips
增加bucket必须之前安装Git,因为bucket都放在GitHub
{% endnote %}

```shell
PS C:\Windows\system32> scoop bucket known
PS C:\Windows\system32> scoop bucket add extras
```

* 安装和设置版本控制工具-Git

安装Git

```shell
# -g 就是来使用前面我们定义的路径
# openssh 是必要组件
PS C:\Windows\system32> scoop install -g git openssh
```

安装Terminus终端模拟器

```shell
# terminus 终端模拟器 这个软件在extras的bucket
PS C:\Windows\system32> scoop install -g terminus
```

设置Terminus默认Shell为Git-Bash

打开Terminus软件,点击齿轮图标

设置: Shell-New Profile-填入下面内容

{% note info %}
Name: Git-Bash
Command: C:\Apps\ScoopApps\apps\git\2.24.1.windows.2\bin\bash.exe
Arguments: --login -i
Environment: TERM=cygwin
{% endnote %}

设置Profile-选择Git-Bash

设置Git

设置01-配置用户名和邮件地址

```bash
$ git config --global user.name "rgonzalez184"
$ git config --global user.email "rgonzalez184@student.cccd.edu"
```

设置02-配置简化命令

```bash
$ git config --global alias.st status
$ git config --global alias.ci commit
$ git config --global alias.co checkout
$ git config --global alias.br branch
```

设置03-配置输出颜色系统

```bash
$ git config --global color.ui true
```

设置04-设置字符集

```bash
$ git config --global core.quotepath false
$ git config --global gui.encoding utf-8
$ git config --global i18n.commit.encoding utf-8
$ git config --global i18n.logoutputencoding utf-8
```

设置05-设置换行符

```bash
$ git config --global core.autocrlf input
$ git config --global core.safecrlf true
```

查看所有全局配置

```bash
$ git config --global --list
```

* 安装和设置NVM和Node.js

安装01-安装NVM

{% note info %}
Tips:
使用原生的 Windows Powershell
管理员运行 Windows Powershell
{% endnote %}

```shell
PS C:\Windows\system32> scoop install -g nvm
```

重启 Windows Powershell

查看所有Node.js版本,我们选择Node.js 12.13.0

```shell
PS C:\Windows\system32> nvm list available
```

安装02-安装Node.js 12.13.0

```shell
PS C:\Windows\system32> nvm install 12.13.0
PS C:\Windows\system32> nvm use 12.13.0
```

验证是否安装成功

```shell
PS C:\Windows\system32> node -v
PS C:\Windows\system32> npm -v
```

* 安装Hexo

切换回Git-Bash进行安装

```bash
$ npm install hexo-cli -g
```

* 新建博客

```bash
$ hexo init blog
```

* 更换主题

```bash
# 我们选择固定的主题版本
$ cd blog
$ git clone https://github.com/theme-next/hexo-theme-next themes/next
```

* 安装编写博客工具-VS Code及插件

```shell
PS C:\Windows\system32> scoop install -g vscode
```

插件:

{% note info %}
* Material Theme
* Material Icon Theme
* Markdown All in One
* Markdown Preview Support
{% endnote %}


### 3.2 配置和运行Hexo 博客

* 新建统一的配置文件,把原来的博客配置文件和主题配置文件的内容都放在里面

```bash
$ mkdir -p blog/source/_data
$ vim next.yml
```

* 配置基本站点信息

```yml
# Site
title: Ronny Blog #网站标题
subtitle: 'Ronny Technical RoadMap' #网站副标题
description: 'Ronny Technical Share' #描述,介绍网站的
keywords: Technical #网站的关键字
author: Ronny Gonzalez #博主姓名
language: zh-CN #语言  zh-CN 是简体中文
timezone: UTC #时区
```

* 配置永久链接

```yml
# URL
url: http://rgonzalez184.cf
```

* 配置主题

```yml
# Extensions
theme: next
```

* 配置主题排版样式

```yml
# Schemes
scheme: Gemini
```

* 配置主题菜单

```yml
# Menu Settings
menu:
  home: / || home
  about: /about/ || user
  tags: /tags/ || tags
  categories: /categories/ || th
  archives: /archives/ || archive

menu_settings:
  icons: true
  badges: false
```

新建对应页面和填充内容

新建tags页面和填充内容

```bash
$ cd blog
$ hexo new page tags
```

```md
---
title: tags #标签
date: 2020-01-03 03:17:48 #时间
type: "tags" #类型一定要为tags
comments: false #提示找个页面不需要评论
---
```

新建categories页面填充内容

```bash
$ cd blog
$ hexo new page categories
```

```md
---
title: categories
date: 2020-01-03 03:18:49
type: "categories"
comments: false
---
```

新建404页面填充内容

```bash
$ cd blog
$ hexo new page 404
```

```md
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>404</title>
</head>
<body>
<script type="text/javascript" src="//qzonestyle.gtimg.cn/qzone/hybrid/app/404/search_children.js" charset="utf-8" homePageUrl="/" homePageName="返回"></script> 
</body></html>
```

新建about页面填充内容

```bash
$ cd blog
$ hexo new page about
```

```md
---
title: about
date: 2020-01-03 03:17:32
comments: false
---
```

* 头像信息设置

```yml
avatar:
  # Replace the default image and set the url here.
  url: images/avatar.png #/images/avatar.gif
  # If true, the avatar would be dispalyed in circle.
  rounded: false
  # If true, the avatar would be rotated with the cursor.
  rotated: true
```

* 社交媒体展示设置

```yml
social:
  GitHub: https://github.com/rgonzalez184 || github
  E-Mail: mailto:rgonzalez184@student.cccd.edu || envelope
```

* 数学公式设置

```yml
# Math Formulas Render Support
math:
  # Default (true) will load mathjax / katex script on demand.
  # That is it only render those page which has `mathjax: true` in Front-matter.
  # If you set it to false, it will load mathjax / katex srcipt EVERY PAGE.
  per_page: true

  # hexo-renderer-pandoc (or hexo-renderer-kramed) required for full MathJax support.
  mathjax:
    enable: true
    # See: https://mhchem.github.io/MathJax-mhchem/
    mhchem: true
```

* 多功能Tag设置

```yml
# Note tag (bs-callout)
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: modern
  icons: true
  border_radius: 3
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0

# Tabs tag
tabs:
  enable: true
  transition:
    tabs: false
    labels: true
  border_radius: 0
```

### 3.3 Push到GitHub仓库

* 注册GitHub账号
* 在本地生成SSH Key和配置Git用的config
* 复制公钥填入GitHub网站
* 测试链接是否成功
* 初始化blog为Git仓库
* 关联远程仓库地址
* Git把文件提交到缓存区
* 填写Git Commit信息
* Push到GitHub远程仓库

### 3.4 GitHub仓库链接Netlify托管平台

* 使用GitHub账号登陆Netlify托管平台
* 新建一个站点,使用blog仓库作为源码
* 填写自定义构建的命令
* 打开Netlify自动生成的链接,能否正常访问

### 3.5 freenom平台注册免费域名

* 注册freenom一个账号
* 注册rgonzalez184.cf免费12个月的域名

### 3.6 Netlify平台域名DNS解析

* 登录freenom平台修改Nameservers为Netlify平台
* 在Netlify平台新建域名rgonzalez184.cf的DNS解析

### 3.7 配置blog的二级域名并绑定个人博客

* 打开站点设置,绑定自定义域名blog.rgonzalez184.cf

## 4 优化和发布博客

### 4.1 优化博客

* 增加HTTPS,等待DNS刷新完成.点击站点设置的HTTPS证书

### 4.2 发布博客

只需要在自己的Hexo的博客目录下新建文章,写文章,Push文章到GitHub仓库就好

## 5 结尾

这就是搭建博客系列01-初始化博客的所有内容,是自己完整梳理和记录搭建博客的过程,用于以后自己使用和给团队新人参考,因为是在中国大陆-新疆搭建的,里面需要解决很多网络问题.里面也有详细描述.后续也有更多搭建博客主题的文章,来讲述自己慢慢坚持写技术博客的过程.

{% note info %}
### Index
Build blog series | 搭建博客系列
Initialize the blog platform | 初始化博客平台
VPS | 服务器
ShadowsocksR(SSR) | 一种协议或客户端名称 
{% endnote %}
