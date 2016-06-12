---
title: Hexo博客搭建简介
date: 2016-05-01 10:17:46
categories: 开发者手册
tags: 
	- blog
	- hexo
---

### 博客搭建方案简介
本博客使用基于node.js开发的静态博客生成工具hexo搭建，部署于国内类github平台 coding.net。

### 使用Hexo工具编写、生成博客
[Hexo](https://hexo.io/) 是一个基于Node.js快速、简单、强大的博客框架,Hexo使用 Markdown语法编写你的文章。 [Hexo](https://hexo.io/) 是一个基于Node.js快速、简单、强大的博客框架,Hexo使用 Markdown语法编写你的文章。

#### 环境依赖
Node.js:[https://nodejs.org/en/](https://nodejs.org/en/)
Git Client:[https://git-scm.com/download/](https://git-scm.com/download/)

#### 安装
使用nodejs的NPM工具安装hexo:
```sh
$npm install -g hexo-cli
```

#### 1.初始化
hexo安装完成你可以使用以下命令初始化Hexo到目标文件夹<folder>。
```sh
$mkdir <folder>
$hexo init <folder>
$cd <folder>
$npm install
```

#### 2.新建博文
```sh
$hexo new 'your title'
```
或：
```sh
$hexo n 'your title'
```
#### 3.生成静态页
```sh
$hexo  generate
```
或：
```sh
$hexo  g
```
#### 4.部署
```sh
$hexo deploy
```
或：
```sh
$hexo d
```
在你正确配置后以上就是使用hexo新建一个博客生成并发布一篇博文的流程，使用组合命令会更加方便。
```sh
$hexo n	<title>	#创建新的页面
#使用自己喜欢的文本编辑器打开新生成的markdown文件
$hexo d -g  #生成并发布
```
使用两行命令就可以完成编写提交并部署到你配置的gitpages了。你也可以选择本地启用http服务,命令如下：
```sh
$hexo server
```
此时hexo会在本地开启一个Http Server默认的端口号为`4000`,浏览器打开`http://localhost:4000/`即可访问。

### 使用coding部署你的静态博客站点
[coding](http://coding.net/) 是国内的类github平台，由于GFW的原因github在国内并不会很稳定所以我选择使用coding来部署我的博客。大致步骤如下：
1. 注册coding账号。
2. 新建一个仓库,如：Blog
3. 本地生成公钥并添加到coding平台。
4. 配置`hexo`根目录下的`_config.yml`文件中的`deploy`节点。如下：
```yml
deploy:
	type: git
	repo: git@git.coding.net:hechun/Blogs.git
	branch: master
```
5. 在coding上选择blog仓库打开`演示`页签配置开启演示功能,在该页中你可以设置一个自己喜欢的coding二级域名比如我的`hechun.coding.io`。
6. 正确的完成以上步骤后便可以在浏览器输入你的coding二级域名访问你的博客啦。

### 最后
以上便是我搭建Hexo静态博客的步骤,当然此片博文并不详细比如git远程参考的配置、coding部署演示页的详细配置都不详尽。写这篇文一者是为了给你一个搭建gitpages的系统印象,再者是我想借此写篇博文尝尝鲜。
