---
layout: post
title: "Overriding jekyll theme defaults"
date: "2020-08-17 15:20 +0800"
tags: jekyll
---

使用`Jekyll new`新建站点后，默认的主题为`minima`，主题相关的一些目录，如`assets`, `_layouts`, `_includes`等不在项目目录中，而是在 Jekyll build 过程中根据 Gemfile 和 Gemfiles.lock 指定的版本读取。这样方便主题开发者更新主题后其他使用这个主题的用户也能容易得应用更新。

要查看主题的文件，可以使用`bundle info --path`命令，如，查看`minima`主题文件的命令如下

```bash
bundle info --path minima
```

该命令会返回 minima 主题文件所在的目录，目录结构如下

```
├── assets
│   ├── main.scss
│   └── minima-social-icons.svg
├── _includes
│   ├── disqus_comments.html
│   ├── footer.html
│   ├── google-analytics.html
│   ├── header.html
│   ├── head.html
│   ├── icon-github.html
│   ├── icon-github.svg
│   ├── icon-twitter.html
│   ├── icon-twitter.svg
│   └── social.html
├── _layouts
│   ├── default.html
│   ├── home.html
│   ├── page.html
│   └── post.html
├── LICENSE.txt
├── README.md
└── _sass
    ├── minima
    │   ├── _base.scss
    │   ├── _layout.scss
    │   └── _syntax-highlighting.scss
    └── minima.scss
```

对于以下目录，Jekyll 会优先查看站点中的内容，在站点目录中新建对应的文件，如`_layouts/home.html`即可覆盖主题中的内容

- `/assets`
- `/_layouts`
- `/_includes`
- `/_sass`
