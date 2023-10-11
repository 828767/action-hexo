---
title: 学术简历样本
date: 2023-02-22 02:02:02
tag: Example
academia: true
---

> 这是个简历示例页，内容源文件：`source/_posts/academia-example.md`，可以修改此文件内容为自己想要的，使用 `Markdown` 或者 `HTML` 语法都可以。

> 如果本页排序在站内靠后，该页内容不会在 `Academia` 主题首页显示，如果遇到不显示的问题，删除其他内容或者将本页排序调整到靠前几页，如：修改本文档 `date` 值：
> 
> ```YML
> date: 2023-8-22 16:59:16    //一般情况下修改这个时间到最新就会排前面
> ```

# About me
This is a simple page for academic website based on Hexo. It just provides a theme frame and all depends on your markdown posts’ styles.

This is the index page which organized with the posts you write in markdown files.

# News
- 2020-04-23: ver 1.2.0 publish, support pjax.
- 2020 February, Join in Test University.
- A new theme for academic page is published.

# Publications
1. Einstein, Albert, Boris Podolsky, and Nathan Rosen. “Can quantum-mechanical description of physical reality be considered complete?.” Physical review 47.10 (1935): 777.
2. Einstein, Albert, Boris Podolsky, and Nathan Rosen. “Can quantum-mechanical description of physical reality be considered complete?.” Physical review 47.10 (1935): 777.

Add more informations in your posts…
# Introduction
This is a light & simple & responsive theme for academic websites on Hexo, crafted from [academicpages](https://github.com/academicpages/academicpages.github.io) on Jekyll. Thanks a lot.

The theme adopts only `post` and `page` in Hexo to show your informations. For an academic page, it's important to be simple and obvious.

Example page: [phosphorw.github.io](https://phosphorw.github.io/)

![mockup](https://raw.githubusercontent.com/PhosphorW/phower-img-folder/master/hexo-theme-academia_mockup.jpg)

## Installation

The simplest way to install is to clone the entire repository:
```BASH
git clone https://github.com/PhosphorW/hexo-theme-academia.git themes/Academia
```

Some required renderers:
```BASH
npm install hexo-renderer-pug hexo-renderer-stylus --save
```

Set theme in hexo work folder's `_config.yml`
```YML
theme: Academia
```

## Create your academic page

Only `post` and `page` are supported in this theme.

```BASH
hexo n post "any title"
```
or
```BASH
hexo n page "any title"
```

**Important:** </br>
Add `academia: true` in front_matter filed in `post .md`.

<img src="https://raw.githubusercontent.com/PhosphorW/phower-img-folder/master/hexo-theme-academia_front-matter.png" width="660px" alt="front_matter">

Only post with `academia: true` front_matter will be shown on home (index) page. You can write your informations in either one post or some posts with this method. The front_matter doesn't works in `page`. The `pages` are standalone with its markdown content.


## Theme Configurtion
All of below options can be config in site folder `_config.Academia.yml`

- Top Menu: in-page anchor, new page links or any links you like
- Side Bar: Support avatar, social links, extra social links (optional), CV_download_link
- Box-shadow mode (optional)

All icons in page is supported with [font-awesome-5](https://fontawesome.com/) (~~font-awesome-4~~)

> fontawesome-4 is not used since v1.2.1. If you want to update manually, first change CDN stylesheet to fa5. Then change your previous icon class `fa` to `fas` or `fas`.

If you need rss feed, use hexo plugin: [hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed)

![theme-layout](https://raw.githubusercontent.com/PhosphorW/phower-img-folder/master/hexo-theme-academia_layout.png)

## Document
中文文档：[Hexo-Theme-Academia 说明文档](https://phower.me/2020/03/Hexo-theme-academia-%E8%AF%B4%E6%98%8E%E6%96%87%E6%A1%A3/)