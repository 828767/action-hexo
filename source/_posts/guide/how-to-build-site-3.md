---
title: '从零开始建个小站 - 本地Git配置'
date: 2022-05-23 20:20:20
categories:
  - 做网站
tags:
  - 教程
---
如果你选择的是自备服务器的付费方案，那么直接在服务器上安装环境部署网站程序即可，本文不做详细演示，下文只针对免费方案进行详细说明。

## 本地 Git 设置

### 安装Git
到 [Git官网](https://git-scm.com/downloads) 下载自己操作系统对应的安装包或者按对应命令安装即可。

#### **Windows**

安装的时候一路选默认 `next` 到底就行，最后会在文件夹右键菜单中出现 `Git Bash Here` 方便使用。

![Git右键菜单](https://cdn.jsdelivr.net/gh/828767/static/images/git_menu_gitbashhere.png)

#### **macOS**

Install [homebrew](https://brew.sh/) if you don't already have it, then:

```
brew install git
```

#### **Linux**

**Debian/Ubuntu**
For the latest stable version for your release of Debian/Ubuntu
```
apt install git
```

**CentOS/Fedora**
```
yum install git
```

### 配置Git用户信息
如前一步图示，随便在哪个文件夹里：点 `右键` 菜单》点击 `Git Bash Here` 》启动 `Git Bash` 「macOS/Linux系统打开 `Terminal（终端）`」，复制粘贴如下命令：

```
# 设置Git用户信息
git config --global user.name "Your_Name"
git config --global user.email "Your_Email"
```
**注意**：请将命令中邮箱及用户名替换为自己实际信息
