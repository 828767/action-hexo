---
title: 网页模板 pug 基本语法
categories:
  - 学编程
tags:
  - 博客建站
date: 2021-12-10 15:22:57
updated: 2021-12-10 15:22:51
toc: true
comments: true
keywords: ''
description: 'pug原名jade，因版权问题更名为pug，即哈巴狗。与hexo默认模块ejs一样，pug也是一个模板引擎，可用于快速的网站开发，当然也可以用于静态博客网站的设计。本站点现时所用主题manupassant也使用了pug。

本文针对Hexo中使用pug的情况为例，说明其基本语法。'
top:
---
# 前言
pug 原名 `jade` ，因版权问题更名为 `pug` ，即哈巴狗。与 hexo 默认模块 `ejs` 一样，pug 也是一个模板引擎，可用于快速的网站开发，当然也可以用于静态博客网站的设计。本站点现时所用主题 manupassant 也使用了 `pug` 。

本文针对 Hexo 中使用 `pug` 的情况为例，说明其基本语法。

# 安装
```sh
# common install
npm install pug

# install for hexo blog
npm install hexo-renderer-pug --save
```

# 语法
pug 不同于 html ，前者不需要标签的开和闭，如 html 的 `<p>Demo</p>` ，在 pug 使用 `p Demo` 即可。

## 缩进
pug 对空格敏感，有点类似 python 对制表符tab敏感。pug 使用空格作为缩进符，当然用 `soft tab` 也可行。同一级标签需保证左对齐。
```pug
div
    p Hello, world!
    p Hello, pug.
```

渲染结果如下：
```html
<div>
    <p>Hellow, world!</p>
    <p>Hello, pug.</p>
</div>
```

## 注释
pug 使用 `//-` 或 `//` 对代码进行注释，前者注释内容不出现在渲染后的 html 文件中，后者反之。
```pug
//- html中不包含此行
// html中会包含此行
```

## 属性
pug 将标签属性存放于括号 `()` 内，多个属性之间以 `逗号` 或 `空格` 分隔。此外，对于标签的 `id` 和 `class` ，pug 使用 `#` 紧跟标签 `id` ,使用 `.` 紧跟标签 `class` ，可以同时设置多个 `class` 。
```pug
h1#title Test title
img#name.class1.class2(src="/test.png" alt="test")
```

渲染结果如下：
```html
<h1 id="title">Test title</h1>
<img id="name" class="class1 class2" src="/test.png" alt="test">
```

## 包含
为了方便代码复用，pug 提供了 `include` 包含功能，以下代码会将 `_partial` 目录下的 `head.pug` 文件内容包含到当前调用的位置。有点 C/C++ 中内联函数的意思。
```pug
doctype html
html(lang='en')
    include _partial/head.pug
```

## 继承
下面是一个简单的 `base` 模板，通过 `block` 定义了页面头部 `head` 和内容 `body` 。块 `block` 有点类似 C/C++ 的抽象函数，需要在继承者中完成定义，填充具体内容。
```pug
//- base.pug
html
    head
        block title
    body
        block content
```

以下文件使用 `extends` 继承以上模板，通过 `block` 覆盖或替换原有块 `block` 。当然，继承者也可以在原有基础上继续扩展。
```pug
//- index.pug
extends base.pug

block title
    title "Test title"

block content
    h1 Hello world!
    block article
```

## 定义变量
pug中通过 `- var name = value` 的形式定义变量
```pug
- var intData = 100
- var boolData = false
- var stringData = 'Test'
p.int= intData
p.bool= boolData
p.stringData= stringData
```

> 需注意的是，在引用变量时，需要在引用位置加上=号，否则会默认将变量名当成普通字符串使用。

如果想要将变量与其它字符串常量或是变量连接在一起，就不能用等号了，而是应该用 `#{}` ，该符号会对大括号内的变量进行求值和转义，最终得到渲染输出的内容。
```pug
- var girl = 'Lily'
- var boy = 'Jack'
p #{girl} is so beautiful!
p And #{boy} is handsome.
```

## 条件结构
pug 的条件语句与其它语言类似，均是如下这般：
```pug
- var A = {value: 'Test'}
- var B = true
if A.value
    p= A.value
else if B
    p= B
else
    p nothing
```

## 迭代
pug 中使用 `each` 和 `while` 实现循环迭代，`each` 可以返回当前所在项的索引值，默认从 `0` 开始计数。
```pug
//- each
ol
    each item in ['Sun', 'Mon', 'Tus', 'Wen', 'Thu', 'Fri', 'Sat']
        li= item

//- get index of each
- var week = ['Sun', 'Mon', 'Tus', 'Wen', 'Thu', 'Fri', 'Sat']
ol
    each item, index in week
        li= index + ':' + item
```
渲染成 html 后：
```html
<ol>
  <li>Sun</li>
  <li>Mon</li>
  <li>Tus</li>
  <li>Wen</li>
  <li>Thu</li>
  <li>Fri</li>
  <li>Sat</li>
</ol>
<ol>
  <li>0:Sun</li>
  <li>1:Mon</li>
  <li>2:Tus</li>
  <li>3:Wen</li>
  <li>4:Thu</li>
  <li>5:Fri</li>
  <li>6:Sat</li>
</ol>
```

`while` 调用方式如下：
```pug
//- while
- var day = 1
ul
    while day < 7
        li= day++
```

## Minix
`mixin` 名曰混入，类似其它编程语言中的函数，也是为了代码复用，可带参数或不带参数，定义方式如下：
```pug
mixin menu-item(href, name)
    li
        span.dot ●
        a(href=href)= name
```
其中，`menu-item` 为调用时所用名称，可认为是函数名，`href` 及 `name` 是参数。同上定义变量所说，`a(href=href)= name` 中第二个 `=` 是为了将后面的 `name` 当作参数来处理，而不是当作字符串 `"name"` 来处理。

调用 `mixin` 定义的代码块，需通过 `+` 号紧跟 `mixin` 名称及参数:
```pug
+menu-item('/Archives','Archives')
+menu-item('/About','About')
```
`mixin` 之所以称为混入，是因为其语法不局限于函数调用，在 `mixin` 可以使用块 `block`
```pug
mixin print(post)
    if block
        block
    else
        p= post

+print("no block")
+print("")
    div.box
        p this is the content of block
```
对应 html 代码：
```html
<p>no block</p>
<div class="box"><p>this is the content of block</p></div>
```

## JavaScript
> 注意以下 `pug` 语句中第一行的 `.` 号。
```pug
script(type='text/javascript').
    var data = "Test"
    var enable = true
    if enable
        console.log(data)
    else
        console.log('nothing')
```

对应的 JS 代码如下：
```js
<script type='text/javascript'>
    var data = "Test"
    var enable = true
    if enable
        console.log(data)
    else
        console.log('nothing')
</script>
```

对于简单脚本，使用 pug 尚可，复杂的还是单独写到 `.js` 文件中，然后通过 pug 引用方便一些，引用方式如下：
```pug
script(type='text/javascript', src='/path/to/js')

//- with hexo function url_for
script(type='text/javascript', src=url_for(theme.js) + '/ready.js')
```
# hexo 相关
在 hexo 主题中使用 pug 时，可以通过使用 hexo 提供的全局变量 `config` ， `theme` 来分别调用博客根目录下 `_config.yml` 文件中的参数以及主题根目录下 `_config.yml` 文件中的参数。
```pug
//- blog config
p= config.description

//- theme config
p= theme.title
```
当然，pug 中可以直接使用 hexo 提供的其它全局变量及辅助函数，使用方法详见 hexo 的文档。

## 示例
```pug
//- head.pug
head
    meta(http-equiv='content-type', content='text/html; charset=utf-8')
    meta(content='width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0', name='viewport')
    meta(content='yes', name='apple-mobile-web-app-capable')
    meta(content='black-translucent', name='apple-mobile-web-app-status-bar-style')
    meta(content='telephone=no', name='format-detection')
    meta(name='description', content=config.description)
    block title
    link(rel='stylesheet', type='text/css', href=url_for(theme.css) + '/style.css' + '?v=' + theme.version)
    link(rel='Shortcut Icon', type='image/x-icon', href=url_for('favicon.png'))
    script(type='text/javascript', src='//cdn.bootcss.com/jquery/3.3.1/jquery.min.js')
    block more
```

```pug
//- base.pug
doctype html
html(lang='en')
    include _partial/head.pug
    block more
        link(rel='stylesheet', type='text/css', href=url_for(theme.plugins) + '/prettify/doxy.css')
        script(type='text/javascript', src=url_for(theme.js) + '/ready.js' + '?v=' + theme.version, async)
    
    //- body
    body: #container.box
        .h-wrapper
            include _partial/nav-menu.pug
        // article content
        block content

        include _partial/footer.pug
```
其中:
- `theme.*` 为主题配置文件 `_config.yml` 中的参数
- `url_for` 为 hexo 提供的用于查找资源路径的函数

# 总结
pug 提供了 `包含` ，`继承` ，`Mixin` 等多种方式用于代码复用，语法简洁易懂，除了初学时需花费一些时间学习各种标点符号的含义外，其它倒也没有太大困难。

当然啦，pug 还有许多其它特性，但就我目前使用情况而言，以上这些便已足够。

## 参考
1. [pugjs.org](https://pugjs.org/zh-cn/api/getting-started.html)
2. [hexo.io/zh-cn/docs/](https://hexo.io/zh-cn/docs/)

## 原文出处
- 作者：litreily
- 链接：https://juejin.cn/post/6844903668383236104
- 来源：掘金
- 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。