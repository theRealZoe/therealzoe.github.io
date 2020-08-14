---
layout: post
title: "Github Pages + Jekyll搭建个人博客"
date: "2020-08-14 09:24 +0800"
tags: jekyll
---

Jekyll 是一个静态站点生成器，内置 GitHub Pages 支持。默认情况下，GitHub Pages 将使用 Jekyll 来构建站点。这里记录下这个博客的搭建过程。

## Installation
我是在VirtualBox中新建了Ubuntu虚拟机，在虚拟机中安装的

首先，需准备Ruby开发环境

```bash
sudo apt install ruby-full build-essential zlib1g-dev
```
可通过以下命令检查是否已安装，ruby版本需在2.5.0或以上版本
```bash
ruby -v
gem -v
gcc -v
g++ -v
make -v
```

然后用 RubyGems 安装 Jekyll和bundler
```bash
gem install jekyll bundler
```

至此，安装完成

## Create a Jekyll site

新建站点，username为github用户名

```bash
git init <username>.github.io
cd <username>.github.io
jekyll new .
```

更新`Gemfile`，使用Github Pages

```bash
# 注释gem "jekyll"
# gem "jekyll", "~> 4.1.1"

# 取消注释gem "github-pages"
gem "github-pages", group: :jekyll_plugins

bundle install
# 执行后提示有版本问题，需执行bundle update
bundle update
```

然后就可以在本地预览了

```bash
bundle exec jekyll serve
```

最后提交代码，准备部署

```bash
git add .
git commit -m 'jekyll default'
```

## Deployment

在github中新建`<username>.github.io`仓库，把站点推送到新建的仓库中，然后就可以在https://username.github.io 中浏览了

```bash
git remote add origin <url>
git push -u orgin master
```

