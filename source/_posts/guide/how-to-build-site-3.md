---
title: '从零开始建个小站 - 1. 搭个本地预览环境'
date: 2022-06-06 20:20:20
categories:
  - 做网站
tags:
  - 教程
---
如果你选择的是自备服务器的付费动态网站方案，那么直接在服务器上安装环境部署网站程序即可，本文不做演示，下文只针对免费静态站方案进行详细说明。

其实官方默认自带的 `hello world` 示例就告知了基本的用法，要把细枝末节展开来还能再写一本书，本教程也只是针对本站部署的方案，给新手演示一个大概的操作流程，更多细节或者高深玩法请在熟悉后自行发掘。

<!-- more -->
虽然也能在线增删改文件，但还是建议拉取仓库到本地电脑进行操作。在本地电脑操作，就有必要搭个本地预览环境。

> 以下以 Windows 系统环境演示，其他操作系统请打开系统终端 terminal 直接输对应的命令


> 到以下涉及软件官网下载如果速度慢，可以从 [墙内淘宝源下载](https://registry.npmmirror.com/binary.html)。

# 1.1 安装 Git 客户端
仓库文件管理借助大名鼎鼎的代码项目管理工具，到 [Git-SCM官网](https://git-scm.com/downloads) 或者 [墙内淘宝源](https://registry.npmmirror.com/binary.html?path=git-for-windows/ "Windows版，其他系统自带或直接命令安装，2023年2月2日最新版本为 v2.39.1.windows.1/") 下载安装包或者软件源默认安装完成即可。

Windows 系统安装完成后，会在右键菜单添加 `Git Bash Here` 入口，方便后续使用。

![Git Bash Here](https://static.yiwangmeng.com/https://raw.githubusercontent.com/828767/static/master/images/git_menu_gitbashhere.png)

如果以前未使用过 Git，一般都需要设置用户名和邮箱，随便一个目录空白地方 点右键》 `Git Bash Here` ，运行以下命令设置：

```bash
git config --global user.name name #设置Git用户名
git config --global user.email "email" #设置Git邮箱
```
> 这里只是最基本的Git信息设置，后续提交同步 GitHub 等需要额外授权，详见站内后文：{% post_link '从零开始建个小站 - 2. 拉取仓库到本地' %}


`Git Bash Here` 这个右键菜单，在哪个目录下点就会将工作路径自动切换到哪，可以省去切换工作路径的麻烦，小白可以多用用。

# 1.2  安装 nodejs
`nodejs` 是跨平台的 JavaScript 运行环境和包管理工具。同样的，到 [Nodejs官网](https://nodejs.org/zh-cn/) 或者 [墙内淘宝源](https://registry.npmmirror.com/binary.html?path=node/) 下载安装包，建议选择长期维护版，默认安装完成即可。

安装完成后，在前文安装完成的 `Git Bash` 或者系统终端中输入命令 `npm version` 验证安装结果：
```JSON
$ npm version
{
  npm: '8.5.5',
  node: '16.15.0',
  ……
}
```

为了后面安装依赖包顺利完成，运行以下命令设置 npm 墙内源：
```BASH
# 设置 npm 墙内源，加快网络下载速度，墙外就不要做了
npm config set registry https://registry.npmmirror.com # 最新淘宝源
npm config set registry http://mirrors.cloud.tencent.com/npm/ # 腾讯源
```

# 1.3 安装 hexo

前文安装完成 `npm` 包管理器后，就可以安装 `hexo` 预览客户端了，打开前文安装完成的 `Git Bash` 或者系统终端，输入以下命令：
```bash
# 系统全局安装hexo，方便从零开始
# macOS 或 Linux 非 root 用户登录需要 sudo 权限运行
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

macOS新版本默认启用的是 `zsh` 终端，`hexo` 安装完成后并未添加到 `zsh` 能识别的系统变量，会出现提示 `zsh: command not found: hexo` 的情况，可添加系统变量解决，具体方法请求助战略合作伙伴 Google和百度，或者就此烂过。

> 也可以 [将系统默认终端改成 `bash`](https://support.apple.com/zh-cn/guide/terminal/trml113/mac)，或者使用后文提到的 VSCODE 集成终端，将 VSCODE 调用默认终端改成 `bash`，然后在 VSCODE 集成终端运行命令即可。

至此，网站预览所需要的系统环境就准备完成。