---
title: '从零开始建个小站 - 1. 搭个本地预览环境'
date: 2022-06-06 20:20:20
categories:
  - 做网站
tags:
  - 教程
---
如果你选择的是自备服务器的付费方案，那么直接在服务器上安装环境部署网站程序即可，本文不做演示，下文只针对免费方案进行详细说明。

其实官方默认自带的 `hello world` 示例就告知了基本的用法，要把细枝末节展开来还能再写一本书，本教程也只是针对本站部署的方案，给新手演示一个大概的操作流程，更多细节或者高深玩法请在熟悉后自行发掘。

<!-- more -->
虽然也能在线增删改文件，但还是建议拉取仓库到本地电脑进行操作。在本地电脑操作，就有必要搭个本地预览环境。

# 1.1 安装 Git 客户端
仓库文件管理借助大名鼎鼎的代码项目管理工具，到 [Git-SCM官网](https://git-scm.com/downloads) 下载安装包或者软件源默认安装完成即可。

Windows 系统安装完成后，会在右键菜单添加 `Git Bash Here` 入口，方便后续使用。

![Git Bash Here](https://cdn.jsdelivr.net/gh/828767/static/images/git_menu_gitbashhere.png)

如果以前未使用过 Git，一般都需要设置用户名和邮箱，随便一个目录空白地方 点右键「Windows系统，其他系统打开系统终端输命令」》 `Git Bash Here` ，运行以下命令设置：
```bash
git config --global user.name name #设置Git用户名
git config --global user.email "email" #设置Git邮箱
```
> 这里只是最基本的Git信息设置，后续提交同步 GitHub 等需要额外授权，详见站内后文：{% post_link guide-how-to-build-site-4 %}

# 1.2  安装 nodejs
跨平台的JavaScript运行环境和包管理工具。一样的，到 [Nodejs官网](https://nodejs.org/zh-cn/) 下载安装包，建议选择长期维护版，默认安装完成即可。

安装完成后，在前文安装完成的 `Git Bash` 或者系统终端中输入命令 `npm version` 验证安装结果：
```bash
$ npm version
{
  npm: '8.5.5',
  node: '16.15.0',
  ……
}
```
# 1.3 安装 hexo
前文安装完成 `npm` 包管理器后，就可以安装 `hexo` 预览客户端了，打开前文安装完成的 `Git Bash` 或者系统终端，输入以下命令：
```bash
# 墙内设置npm淘宝源，加快下载速度
npm config set registry https://registry.npm.taobao.org
# 系统全局安装hexo
npm install -g hexo-cli
```
安装完成后可使用命令 `hexo version` 验证：
```bash
$ hexo version
INFO  Validating config
hexo: 6.2.0
hexo-cli: 4.3.0
……
```

至此，网站预览所需要的环境就准备完成。