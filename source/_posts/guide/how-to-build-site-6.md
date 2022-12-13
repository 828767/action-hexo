---
title: '从零开始建个小站 - 4. 练手内容维护'
date: 2022-05-22 20:20:20
categories:
  - 做网站
tags:
  - 教程
---

本实操仅针对 {% post_link guide-how-to-build-site-2 "建站方案选择" %} 中提及的免费方案：**hugo/hexo + GitHub + GitHub免费二级域名/自备域名** ，另外的付费方案自带网站后台，界面化的一体操作没什么好演示的，如有需要可求助我们的战略合作伙伴Google和百度。

针对 GitHub 仓库版方案，我们 **`只需要对私有源码仓库`** 做两件事：`增/删/改` --> `Git提交同步`

![内容增删改](https://cdn.jsdelivr.net/gh/828767/static/images/github-zsg.png)

- 增：新增文章、页面、图片等
- 删：删除文章、页面、图片等
- 改：对已有的文章、页面、配置等进行修改

> **除非你会，否则不要动主题目录下任何东西**，主题功能只需要按主题文档修改 `_config.主题名.yml` 中配置即可。

> **除非你会，否则不要动主题目录下任何东西**，主题功能只需要按主题文档修改 `_config.主题名.yml` 中配置即可。

> **除非你会，否则不要动主题目录下任何东西**，主题功能只需要按主题文档修改 `_config.主题名.yml` 中配置即可。

使用本站提供的项目仓库自动方案，提交源代码后，会自动触发渲染发布，然后需静待上端网络缓存更新后才看到最新结果。

强调三点：
1. 所有的增删改都需要同步到上端仓库后网络上才能看到变更！！！
2. 所有的增删改都需要同步到上端仓库后网络上才能看到变更！！！
3. 所有的增删改都需要同步到上端仓库后网络上才能看到变更！！！

## 4.1 新建文章
新建文章或页面可以通过新建命令或者复制已有范本后再修改，任意方式都可以，只要最终生成符合规则的MarkDown文档即可。

### 4.1.1 **`hexo n` 文件名**
命令方式新建文章或页面，那必定需要在命令终端内执行。

打开命令行终端，输入：`hexo n post-name` ，如：`hexo n just-a-test` ，就会在 `source/_post` 目录下生成一个名称为 `just-a-test.md` 的文件，这就是新文章的 MarkDown 源码了。

> 生成的新文章源码名称不建议含有特殊符号、汉字

打开源码文件就能看到自动生成了文章标题等基本的 `Front-matter` 信息，文章标题等按自己的实际内容编写修改。

### 4.1.2 **复制已有再修改**
`复制已有` 就是字面意思，不用打开命令行终端输命令，直接到 `source/_post` 目录下找个已存在的 MarkDown 文件，如：把网站自带的 `hello-world.md` 这个文件**复制一份改名**为 `new-post.md` ，然后打开该源码文件，把标题，日期等信息按实际内容需求改好，填充新内容就成了。

## 4.2 **格式！格式！**
前文新建文章或页面说明都提到了需要遵循格式。

一个MarkDown 源码文件，除了 `Front-matter` 头部信息，其他的就是基本的 MarkDown 语法，MarkDown 语法是页面内容展示，错误与否都只是关系到展示内容样式，而 `Front-matter` 则直接关系到 hexo 能不能把 MarkDown 源码文件正确渲染成 HTML ，所以遵循正确的 `Front-matter` 至关重要。

![新建文章示例](https://cdn.jsdelivr.net/gh/828767/static/images/hexo-edit.gif)

不管是Hugo还是Hexo，他们都只是一种渲染框架，所以MarkDown源代码都需要特定的 `Front-matter` 标记，也就是两行 `---` 中间的那段。
```yml
---
title: '网页模板 pug 基本语法'
categories: 学编程
tags:
  - 博客建站
date: 2021-12-10 15:22:57
updated: 2021-12-10 15:22:51
toc: true
comments: true
keywords: ''
description: 'pug原名jade，因版权问题更名为pug，即哈巴狗。如果 `Front-matter` 内容

有跨行或特殊符号等，请用英文引号包起来，就如本段示例。'
top:
---
这里开始就是正文内容了……
```
以上示例是 Hexo 程序的 `Front-matter` 头部信息，其中一些设置项也需要对应的主题支持，如果不是 Hexo 基础 `Front-matter` ，具体需要添加什么根据主题文档来。

> 注意：每一个参数的 : 或者 - 后，都需要至少留一个空格，如果不填值就无所谓，或者将参数行删除都行，就是不能不留空格直接写，否则会报错，格式有错误时 VSCODE 也会显色提示，请留意。

`Front-matter` 基础配置项可见：
1. [Hugo-Front-Matter](https://gohugo.io/content-management/front-matter/)
2. [Hexo-Front-matter](https://hexo.io/zh-cn/docs/front-matter)

在完成了 `Front-matter` 信息设定后，我们就可以在第二个 `---` 行下方填充自己想要的内容。内容书写格式默认使用 MarkDown 语法，你直接写 HTML 代码也行，甚至你可以不顾语法当记事本或者Word写是没问题的，无非就是少了些格式样式。
> MarkDown 语法边用边学都没问题，本来就没几个语法，可参考 {% post_link guide-how-to-build-site-8 %} 中 `MarkDown语法` 章节

## 4.3 提交同步数据
对于增删改后的内容，我们可以启动本地预览查看效果，没问题了再通过 Git 提交并推送到上端仓库，静待上端渲染及刷新完缓存就能看到最终结果了。
> 本地预览方法请参见 {% post_link guide-how-to-build-site-4 %} 中 `预览测试` 章节内容

> Git 提交同步数据可用命令行，也可以使用 VSCODE 集成的界面化操作，详情请参考：{% post_link guide-how-to-build-site-5 %}


## 4.4 使用快速模板

在熟悉了 Hexo 的基础用法后，有些内容是制式固定的，或者想偷个懒一次性都添加好默认内容，那么我们就可以借助自定义快速模板来完成。

在使用 `hexo n` 命令新建文章时，其实是遵循模板规则。打开 `scaffolds` 目录，可见有文章，页面等模板文件，打开源码可见如下内容

```yml
---
title: {{ title }} //自动替换标题
date: {{ date }} //创建时间
tags:	//没内容就留空，但该 tags: 项会创建
---
```

比如在 `post.md` 添加新内容如下：

```yml
---
title: {{ title }}
date: {{ date }}
tags:
   - Linux
   - Windows
top:
---
```

那么，在 `hexo n post just-a-test` 命令执行后，生成的新文章默认就会带上新加内容，其他用法以此类推。
