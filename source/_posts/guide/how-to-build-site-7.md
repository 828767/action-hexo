---
title: '从零开始建个小站 - 5. 个性化设置'
date: 2022-05-21 20:20:20
update: 2025-2-26 11:21:42
categories:
  - 做网站
tags:
  - 教程
---
项目仓库克隆下来，网站的各项设置都是默认的，一些标题，作者之类的需要根据自己的实际情况进行修改，个性设置主要是网站根目录的网站基础配置和主题配置。

好在 `hugo` 和 `hexo` 配置结构大同小异，而且都支持将配置文件放在网站根目录下，只需要修改配置，今后主题更新只需要同步配置其他也互不影响。
<!-- more -->
# 5.1 认识文件
```bash
action-hexo    #hexo程序工作目录
|   README.md #说明文档
|   .gitignore  #指定Git提交时忽略的文件规则
|   package.json  #依赖包记录，不要动
|   _config.yml  #网站基础配置文件，定义网站标题，作者等
|   _config.fluid.yml  #fluid这个主题的配置文件，来源于且优先级高于主题目录下的_config.yml
|
+---node_modules  #hexo的依赖环境，不要动，一般都会添加到.gitignore忽略
+---scaffolds  #文章/页面/草稿模板，不会就不要动
|
+---source  #网站内容根目录，网络路径为：/
|   favicon.ico #网站图标，网络路径为：/favicon.ico
|   \---images  #自建文件夹用来放图片资源，网络路径为：/images
|   |   GoodHexo.png  #/images下的图片，引用地址为：/images/GoodHexo.png，也可以相对路径：../images/GoodHexo.png
|   \---_posts  #你所有的文章都存在这个目录底下
|   |   hello-world.md  #示例文章源文件，该MarkDown文件会被hexo渲染成HTML页发布
|   \---about  #自建的一个叫 about 的页面目录
|   |   index.md  #about 页面内容，网络路径为：/about/
|   |
+---themes  #主题存放目录
|   \---landscape #默认主题
|   \---butterfly #本地另一个主题
|   \---fluid #本地另一个主题
|   |
```
![认识hexo文件](https://static.yiwangmeng.com/https://raw.githubusercontent.com/828767/static/master/images/hexo-files-tree.png "Hexo 项目文件结构")

# 5.2 网站设置
从上文可知，网站基础配置需要在 `hexo程序工作目录` 中的 `_config.yml` 进行配置：
```yml
# Site
title: 易网盟 #网站标题
subtitle: '专注网站建设优化' #网站副标题
description: 'Hexo + GitHub免费仓库托管方案，微软不倒，羊毛到老！' #网站描述
keywords: 静态网站  #网站关键词，不是所有的主题都支持
author: 易网盟  #作者
timezone: 'Asia/Shanghai' #时区，一般中国时区
# language: en  #网站语言，默认 en，请根据主题文档设置
language: zh-CN

# URL
## Set your site url here. For example, if you use GitHub Page, set url as 'https://username.github.io/project'
url: https://yiwangmeng.cn # 网址必须以 http[s]:// 开头，没有自己的域名就用免费 username.github.io
permalink: :title.html #链接发布格式
```
打开查看内容就能知道大概了，都有对应的注释，请根据自己实际情况修改填写，或者可以参阅 [官方配置文档](https://hexo.io/docs/configuration.html)。
> 如果网站网址是配置自有域名，请在域名解析托管商添加对应 `CNAME` 解析，可参考：{% post_link '从零开始建个小站 - 常见问题' %} 中相关章节：`要修改网址怎么办`。
# 5.3 主题设置
首先在上文 [网站设置](#5-2-网站设置) 中切换启用自己喜欢的主题，行首以 `#` 开头表示注释掉了不启用：
```yml
# Extensions 
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
# 只能启用1个主题，启用后本地使用 `hexo server` 命令即可启动预览服务进行预览
# 切换主题后如果预览样式不对，请启动预览服务前运行一遍 `hexo clean` 命令
# theme: landscape  #默认主题，最简单
# theme: maupassant #简洁的博客主题，配置文件：_config.maupassant.yml
theme: butterfly  #时尚的博客主题，配置文件：_config.butterfly.yml
# theme: matery #响应式布局多媒体主题，配置文件：_config.matery.yml
# theme: fluid #Material Design 风格主题，配置文件：_config.fluid.yml
# theme: next #简约的博客主题，配置文件：_config.next.yml
# theme: Academia #学术简历主题，配置文件：_config.Academia.yml
# theme: yelee #双栏博客主题，配置文件：_config.yelee.yml
```

接下来就对指定的主题进行配置，具体到主题功能设置每个主题都不一样，所以需要根据实际使用的主题文档去配置，一般在主题目录下都会有个 `README.md` ，请打开或者找到主题在线文档去阅读，主题让装啥就装啥，让咋改就咋改。

为了以后更新主题时不覆盖我们已经配置好的内容，可以将主题目录下的 `_config.yml` 复制到 `hexo根目录` 下，并重命名为：`_config.主题名.yml` ，如：`_config.fluid.yml` 。

> `_config.主题名.yml` 来源于 `themes/主题名/_config.yml` 或 `node_modules/hexo-theme-主题名/_config.yml`，如主题有更新请自行同步

> Hexo 会将 `_config.主题名.yml` 和主题目录下的 `_config.yml` 配置内容 **合并**  **合并**  **合并** 使用，相同配置项则以 `_config.主题名.yml` 中的值为准


然后按照主题说明文档在新复制的主题配置中按需进行配置，以后主题有更新，如果涉及到该配置文件变更，请将最新内容同步到 `_config.主题名.yml` 中即可。