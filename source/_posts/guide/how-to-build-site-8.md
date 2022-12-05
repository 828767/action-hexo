---
title: '从零开始建个小站 - 6. 其他知识'
date: 2022-05-21 20:00:00
categories:
  - 做网站
tags:
  - 教程
---
想到什么写什么，如果没有你关心的问题，请一如既往的求助本站战略合作伙伴 Google和百度。
<!-- more -->
# 6.1 学会基本的 Git
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

> 打开 `.gitconfig` 文件可见之前配置的用户名称和email信息等，直接通过编辑配置文件和通过命令设置理是一样的效果。

# 6.2 hexo高级语法
如果只是普通的写写博客，做个小展示网站什么的，高级语法也不需要。但用上些高级语法，功能就更强大，在处理大量同质内容时就事半功倍了，直接见官方文档吧：
1. [Hexo：标签插件（Tag Plugins）](https://hexo.io/zh-cn/docs/tag-plugins)
2. [Hexo：数据文件（data-files）](https://hexo.io/zh-cn/docs/data-files)

# 6.3 MarkDown语法
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

## References

1. [Markdown 入门参考](http://xianbai.me/learn-md/article/about/readme.html)
2. [Markdown 基本语法](https://markdown.com.cn/basic-syntax/)
3. [Markdown 菜鸟教程](https://www.runoob.com/markdown/md-tutorial.html)