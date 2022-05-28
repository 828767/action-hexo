---
title: '从零开始建个小站 - 实操：本地测试预览'
date: 2022-05-29 20:20:20
categories:
  - 做网站
tags:
  - 教程
---
如果你想在本地就直接看到渲染后的效果，那么还需要安装个本地环境。

## Hugo
Hugo 是个golang开发的跨平台程序，无需外部依赖，直接将单程序安装部署在本地就行，此处以Windows操作系统为示例，其他操作系统请见 [Hugo官方安装说明][hogo-install]。

打开 [Hugo版本发布页](https://github.com/gohugoio/hugo/releases)，下载 Windows 版本，建议下载 [hugo_extended 版](https://github.com/gohugoio/hugo/releases/download/v0.99.1/hugo_extended_0.99.1_Windows-64bit.zip)，将程序 `hugo.exe` 解压到某目录，如 `C:\HUGO\` ，然后将此目录添加到系统变量中就可以在任何位置直接执行 `hugo` 命令，可直接打开命令终端使用 `set` 一键完成：
```
# 将 C:\HUGO\ 添加到系统 path 变量，请替换成自己的实际路径
set path=%path%;C:\HUGO\
```
如果习惯界面设置，可以百度搜索：`Windows 添加path变量` ，设置完成后任意路径下执行命令可见效果：
```
$ hugo version
hugo v0.99.1-d524067382e60ce2a2248c3133a1b3af206b6ef1+extended windows/amd64 BuildDate=2022-05-18T11:18:14Z VendorInfo=gohugoio
```

切换到刚克隆下来的项目仓库「vscode打开文件夹后启动的终端会自动切到当前目录」，预览下网站效果：
```
xxx@CVE MINGW64 /d/git/action-hugo (main) //当前所在路径，Git分支
$ hugo server //运行本地服务端
Start building sites … 
hugo v0.99.1-d524067382e60ce2a2248c3133a1b3af206b6ef1+extended windows/amd64 BuildDate=2022-05-18T11:18:14Z VendorInfo=gohugoio

                   | ZH | EN  
-------------------+----+-----
  Pages            | 20 | 19
  Paginator pages  |  0 |  0
  Non-page files   |  0 |  0
  Static files     |  6 |  6
  Processed images |  0 |  0
  Aliases          |  2 |  1
  Sitemaps         |  2 |  1
  Cleaned          |  0 |  0

Built in 352 ms
Watching for changes in D:\git\action-hugo\{archetypes,content,data,layouts,static,themes}
Watching for config changes in D:\git\action-hugo\config.toml, D:\git\action-hugo\themes\ananke\config.yaml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```
点击返回提示的url调用浏览器打开即能看到效果。

## Hexo

Hexo 需要依赖 `npm` ，所以需要安装 `nodejs`，直接到 [官网](https://nodejs.org) 下载安装包一路默认安装，macOS及Linux按官网提示安装即可。安装完成 `npm version` 有相应提示。

因为要在本地运行查看效果，那么还需要安装 `hexo-cli` 和 `node_modules` 依赖：
```
xxx@CVE MINGW64 /d/git/action-hexo (main) //当前所在路径，Git分支
$ npm install -g hexo-cli //全局安装hexo客户端
$ npm install //在hexo仓库根目录下执行，会自动安装预设的模块
```
安装完成后，执行 `hexo version` 可以查看效果：
```
xxx@CVE MINGW64 /d/git/action-hexo (main) //当前所在路径，Git分支
$ hexo s
INFO  Validating config
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/ . Press Ctrl+C to stop. 
```
点击返回提示的url调用浏览器打开即能看到效果。
