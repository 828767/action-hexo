---
title: '从零开始建个小站 - 其他知识'
date: 2022-05-21 20:00:00
categories:
  - 做网站
tags:
  - 教程
---
想到什么写什么，如果没有你关心的问题，请一如既往的求助本站战略合作伙伴 Google和百度。
<!-- more -->
# 学会基本的 Git
不管是敲代码还是码字工，大名鼎鼎的 Git 都应该学一点，团队一起码代码，汇聚天下豪杰一起写流水小说，事后回查都游刃有余。
## Git 基础
网络上优秀教程一大片，不浪费时间精力了，随便找一个：[Git 教程 | 菜鸟教程](https://www.runoob.com/git/git-basic-operations.html)，边用边学就行，俺们也是这样过来的。

## 改了文件名大小写，Git 不会显示变更无法提交
Git 默认对文件名大小写不敏感，即便你把一个文件名从 `a.conf` 改成 `A.CONF` ，Git 也认为没有变更，所以也就无法将此变更提交同步到仓库，需要在项目仓库路径下运行以下命令禁用忽略大小写：
```bash
git config core.ignorecase false
```

设置完就对大小写敏感了，此时更改文件名大小写就能提交变更了。

## 让 Git 通过代理连接
有些地区直接无法连接全球男性交友社区，也就无从谈起仓库增删改，就需要借助代理连接，可通过以下命令指定Git走代理网络：
```bash
#这里使用socks5 端口为1080，具体端口看代理软件配置
git config --global http.proxy 'socks5://127.0.0.1:1080' 
git config --global https.proxy 'socks5://127.0.0.1:1080'
```

查看代理：
```bash
git config --global --get http.proxy
git config --global --get https.proxy
```

取消代理：
```bash
git config --global --unset http.proxy
git config --global --unset https.proxy
```

或者也可以通过编辑 Git 配置文件直接配置，打开 `用户目录/.gitconfig` ，Windows系统如 `C:\Users\ywm\.gitconfig` ，增加如下内容：
```toml
# 这是个使用 clash 代理的默认端口示例，具体请看代理软件配置
[core]
	gitproxy = socks5://127.0.0.1:7890
[http]
	postBuffer = 524288000
	postBuffer = 524288000
	proxy = socks5://127.0.0.1:7890
[https]
	postBuffer = 524288000
	postBuffer = 524288000
	proxy = socks5://127.0.0.1:7890
```

> 打开 `.gitconfig` 文件可见之前配置的用户名称和email信息等，直接通过编辑配置文件和通过命令设置是一样的效果。

以上是针对 `http[s]://` 协议的代理设置方式，一般 `ssh://` 协议链接不需要代理，如果需要，可以参考此教程去设置：[Git 通过配置SSH代理访问 Github](https://segmentfault.com/a/1190000021998129 "懒得写教程，自己到此去仔细看")

## 添加/删除 `submodule`
本仓库包中自带的 Hexo 主题都是通过 `git submodule add` 管理的，主题只是作为一个版本链接提交，源码仓库中 `themes` 目录下并不包含主题文件。
> 以 `submodule` 方式管理的文件是不能直接在主仓库进行增删改操作的，改了会出现 `Subproject commit xxxx-dirty` 提示，线上使用时将会出现找不到 `submodule` 版本的错误

如果想添加其他的主题，可以将主题文件提交，作为仓库项目的一部分，也可以以 `submodule` 方式应用，添加只需要一条命令：
```Bash
git submodule add --depth=1 主题仓库地址 themes/主题名
```

这样该主题文件夹只是以一个指定版本链接的形式存在于本仓库项目中，如果想完整下载到本地，添加 `--recurse-submodules` 参数就能一起克隆：
```Bash
git clone --recurse-submodules 源码仓库地址 #带子模块一起克隆到本地
```

如果不需要其中某个主题，可以通过以下方法删除掉，以删除 `themes/ananke` 这个主题为例：
1. 删除 `.gitmodules` 中这部分
   ```toml
   [submodule "themes/ananke"]
	path = themes/ananke
	url = https://github.com/theNewDynamic/gohugo-theme-ananke.git
   ```
2. 删除 `.git/config` 中以下部分
   ```toml
   [submodule "themes/ananke"]
	url = https://github.com/theNewDynamic/gohugo-theme-ananke.git
	active = true
   ```
3. 删除 `.git\modules\themes` 目录下的 `ananke` 文件夹
4. 删除 `themes\ananke` 文件夹
5. 在 Git 中将以上变更暂存
6. 在项目根目录路径下运行 `git rm --cached themes\ananke` 命令清理 Git 工作区缓存

至此，该 `submodule` 就从版本库中删除了，将所有变更结果提交同步到线上仓库即可。

## Git 回滚到指定版本
1. 在 `仓库文件夹下` 打开 `Git Bash Here` 输入 `git reflog` 命令，会返回这样的历史提交记录：   
	```Bash
	ef39b2d (HEAD -> main, origin/main, origin/HEAD) HEAD@{0}: commit: update
	fa646fe HEAD@{14}: commit: 角色管理站点权限不可编辑bug修改
	60b35d4 HEAD@{15}: commit: 拓扑图相关修改9
	3173e7a HEAD@{16}: commit: 拓扑图相关修改8
	d51db77 HEAD@{17}: commit: 拓扑图相关修改8
	```
2.  按 `q` 「英文状态下」退出 log 记录，然后输入回退到指定版本命令：`git reset xxx`，`xxx` 指某次提交的版本记录 `id`，如：
	```Bash
	# 添加 `--hard` 参数会将工作区变更全部擦除
	git reset --hard 3173e7a
	```
3. 强制推送至远程：输入命令 `git push --force`，至此版本回退就成功了

# Hexo 高级用法
如果只是普通的写写博客，做个小展示网站什么的，高级语法也不需要。但用上些高级语法，功能就更强大，在处理大量同质内容时就事半功倍了，直接见官方文档吧：
1. [Hexo：标签插件（Tag Plugins）](https://hexo.io/zh-cn/docs/tag-plugins)
2. [Hexo：数据文件（data-files）](https://hexo.io/zh-cn/docs/data-files)


Hexo标签语法能够快速实现一些功能，但并不是所有的主题都支持，当在内容中使用了标签语法，而主题不支持时，将出现渲染失败异常，如下面这段 `ButterFly` 主题支持的图库代码：
```HTML 
<div class="gallery-group-main">
{% galleryGroup '自带主题' '主题预览截图' '/gallery/' https://i.loli.net/2019/11/10/T7Mu8Aod3egmC4Q.png %}
</div>
```

切换到其他主题要么功能未实现，要么直接渲染出错异常，需要删除对应的内容方可。

# MarkDown 语法
## 📌 **Titles**

- Heading 1: `# A first-level title`
- Heading 2: `# A second-level title`
- Heading 3: `## A third-level title`


## 💻 **Code blocks**
`creates a new code block.`，源码如下：
```MarkDown
`creates a new code block.`
```

` ```py ` creates a new code block with Python syntax highlighting.


## **📋** **Lists**

We automatically detect ordered and un-ordered lists as you type. 

Begin a line with `- ` or `* ` to start a bullet list.  
Being a line with `1. ` to start a numbered list. Use `Tab` to go one level deeper, and `Shift+Tab` to go up. Begin a line with `- [ ] ` to start a task list.


## **🎤** **Quotes**

Begin a line with `> ` to create a block quote.

## **🐮** **emoji markup**
😊 	_😃_ 	😴

[Complete list of github markdown emoji markup](https://gist.github.com/rxaviers/7360908)

[另一个emoji表情大全](https://www.emojiall.com/zh-hans/all-emojis)

## **💖** **Images**
```Markdown
![图片alt](图片链接 "图片title")
```
图片链接有两种方法引用，任意一种都可以，各有利弊，自行选择。

方法1：上传到图床，然后通过图床地址引用

```Markdown
#图床就是别人提供给你的存储空间和网络
![图床引用](https://s1.ax1x.com/2022/12/06/z6rzA1.jpg "imgse图床引用示例")
```

方法2：图片文件存在项目内，本地引用

```MarkDown
#相对路径：相对于本文档的路径，`..` 表示上级目录
#这种写法在MarkDown编辑器中可以实时预览效果
![自存相对路径引用](../../images/hexo.jpeg "图片引用示例")
#绝对路径：引用网络路径，未经网络解析无法预览，但发布到网络上是正确的
![自存绝对路径引用](/images/hexo.jpeg "图片引用示例")
```

`Hexo` 项目 `/source` 目录为网络根路径 `/` ，本地文件 `/source/images/hexo.jpeg` 在网络上对应的 url 为：`https://yiwangmeng.cn/images/hexo.jpeg`

## References

1. [Markdown 入门参考](http://xianbai.me/learn-md/article/about/readme.html)
2. [Markdown 基本语法](https://markdown.com.cn/basic-syntax/)
3. [Markdown 菜鸟教程](https://www.runoob.com/markdown/md-tutorial.html)