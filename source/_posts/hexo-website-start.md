---
title: Hexo 搭建教程
categories: 教程
tags: Hexo
---

因自有服务器到期，于是把博客转移到gitpage托管，毕竟免费，一年可以少花几百块钱

本博客用Hexo搭建，主题是Next

曾搭建过WordPress， dz等动态博客， 也试过Jekyll等静态博客

总体来说还是Hexo流程更简单一些，更易于自定义与维护，也能让人更安心写作，而不去鼓捣杂七杂八的插件

**注意： 以下教程基于Hexo v3.3.9**

### Step1 安装必要的软件包

- 安装Hexo

``` bash
$ sudo npm install -g hexo
```
- 安装部署到GitHub的工具

``` bash
$ npm install hexo-deployer-git --save
```

<!-- more -->

### Step2 初始化与设置

- Hexo初始化

``` bash
$ mkdir blog
$ cd blog
$ hexo init
```

- 建立Git仓库

在GitHub先创建一个repo， 名称任意
``` bash
$ git init
$ git remote add origin <你的GitHub仓库地址>
$ git add .
$ git push origin master -f
```

- 修改部署配置项

在你当前目录下找到`_config.yml`文件，编辑器打开

修改以下配置项

``` yml
url: <你的GitHub用户名>.github.io/<博客项目仓库名>
root: /<博客项目仓库名>/

deploy:
  type: git
  branch: gh-pages
  repo: <你的GitHub仓库地址>
```


- 部署静态博客

``` bash
$ hexo g
$ hexo d
```

至此博客基本部署完毕， 打开`<你的GitHub用户名>.github.io/<博客项目仓库名>`这个网址即可访问刚建好的博客了

### Step3 个性化配置

- 修改博客主题

hexo的默认主题是landscape，界面简单但也没什么特色

hexo更换主题非常容易，想知道当前都有哪些漂亮的主题，可以到hexo的官网挑选

主题文件下载至themes文件夹下即可，以我使用的next主题为例：

``` bash
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```

然后需要修改博客目录下的`_config.yml`文件

``` yml
theme: next
```

然后需要重新部署，以后每次更新文章、配置、主题都需要按以下步骤部署

``` bash
$ hexo clean #这一步可以省略，但是容易出现样式不对的小问题
$ hexo g
$ hexo d
```

修改配色方案，文本布局，字体图标等UI调整都是在主题文件夹下的`_config.yml`文件里改动，具体的参数规则参考主题的官方文档，这里不再赘述