---
title: '从零开始建个小站 - 实操：内容增/删/改'
date: 2022-05-31 20:20:20
categories:
  - 做网站
tags:
  - 教程
---

- 增：新增文章、页面、图片等
- 删：删除文章、页面、图片等
- 改：对已有的文章、页面等进行修改

**所有的增删改都需要提交到线上仓库才能看到改变**。使用本站提供的项目仓库，提交源代码后，会自动触发渲染发布，然后静态上端网络缓存更新后才能看到最新结果。

### 注意格式
不管是Hugo还是Hexo，他们都只是一种渲染框架，所以MarkDown源代码都需要特定的 `Front-matter` 标记，也就是两行 `---` 中间的那段。
```
---
title: '网页模板 pug 基本语法'
categories:
  - 学编程
tags:
  - 博客建站
date: 2021-12-10 15:22:57
updated: 2021-12-10 15:22:51
toc: true
comments: true
keywords: ''
description: 'pug原名jade，因版权问题更名为pug，即哈巴狗。与hexo默认模块ejs一样，pug也是一个模板引擎，可用于快速的网站开发，当然也可以用于静态博客网站的设计。本站点现时所用主题manupassant也使用了pug。'
top:
---
```
以上 `Front-matter` 是 Hexo 程序的，其中设置项也需要对应的主题支持，如果不是 Hexo 基础 `Front-matter` ，具体需要添加什么根据主题文档来。

`Front-matter` 基础配置项可见：
1. [Hugo-Front-Matter][]
2. [Hexo-Front-matter][]


[Hexo-Front-matter]: https://hexo.io/zh-cn/docs/front-matter
[Hugo-Front-Matter]: https://gohugo.io/content-management/front-matter/ "Front Matter Formats"
