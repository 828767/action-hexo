---
title: 学术简历样本
date: 2022-02-22 02:02:02
tag: Example
academia: true
---
> 这是个学术简历示例，内容源文件：`source/_posts/academia-example.md`

> 如果本页排序在站内靠后，该页内容不会在 `Academia` 主题首页显示，不知道为何，如果遇到不显示的问题，删除其他内容或者将本页排序调整到靠前几页

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

## Preparation

Some skills you need:
- Publish a Hexo blog: [Learn more](https://hexo.io)
- Git
- Markdown: [Learn more](https://www.appinn.com/markdown/#list)
- Deploy a server (Optional)
- Balabala...

## Installation

The simplest way to install is to clone the entire repository:
```
git clone https://github.com/PhosphorW/hexo-theme-academia.git themes/Academia
```

Some required renderers:
```
npm install hexo-renderer-pug hexo-renderer-stylus --save
```

Set theme in hexo work folder's `_config.yml`
```
theme: Academia
```

## Create your academic page

Only `post` and `page` are supported in this theme.

```
hexo n post "any title"
```
or
```
hexo n page "any title"
```

**Important:** </br>
Add `academia: true` in front_matter filed in `post .md`.

<img src="https://raw.githubusercontent.com/PhosphorW/phower-img-folder/master/hexo-theme-academia_front-matter.png" width="660px" alt="front_matter">

Only post with `academia: true` front_matter will be shown on home (index) page. You can write your informations in either one post or some posts with this method. The front_matter doesn't works in `page`. The `pages` are standalone with its markdown content.


## Theme Configurtion
All of below options can be config in theme folder `_config.yml`

- Top Menu: in-page anchor, new page links or any links you like
- Side Bar: Support avatar, social links, extra social links (optional), CV_download_link
- Box-shadow mode (optional)

All icons in page is supported with [font-awesome-5](https://fontawesome.com/) (~~font-awesome-4~~)

> fontawesome-4 is not used since v1.2.1. If you want to update manually, first change CDN stylesheet to fa5. Then change your previous icon class `fa` to `fas` or `fas`.

If you need rss feed, use hexo plugin: [hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed)

![theme-layout](https://raw.githubusercontent.com/PhosphorW/phower-img-folder/master/hexo-theme-academia_layout.png)

### Update Theme
This theme supports `data files` smooth update. Copy `_config.yml` in theme folder to site folder `/source/_data/theme.yml`, if there is no `_data` folder, create it.

Then you can modify your theme configuration in the mentioned `theme.yml`. If there is any update, just pull the new branch and your configurations won't be merged. 

**Note:**
1. When use `data files` to config theme, you must restart hexo server after any modifictions. `hexo server` again.
2. Sometimes there will be changes in theme `_config.yml`, please refer to [release page](https://github.com/PhosphorW/hexo-theme-academia/releases) for more details before update.

## Document
中文文档：[Hexo-Theme-Academia 说明文档](https://phower.me/2020/03/Hexo-theme-academia-%E8%AF%B4%E6%98%8E%E6%96%87%E6%A1%A3/)