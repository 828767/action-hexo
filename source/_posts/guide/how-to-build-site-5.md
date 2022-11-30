---
title: '从零开始建个小站 - 3. 搞个编辑器'
date: 2022-05-23 20:20:20
categories:
  - 做网站
tags:
  - 教程
---

工欲善其事必先利其器，一个好用的编辑器可以事半功倍。
<!-- more -->
# 3.1 下载安装编辑器
VSCODE 就是个不错的选择，自行到 [微软官方网站](https://code.visualstudio.com/download) 去下载安装，优点：
1. 全目录管理，一个界面可以管理整个目录下的文件
2. 语法格式显示，也能实时预览
3. 与Git集成，可以界面化操作Git提交同步，比较等
4. 集成命令终端，预览调试方便
 
![VSCODE](https://cdn.jsdelivr.net/gh/828767/static/images/vscode-hexo.png)

其他如 Atom、Sublime Text、Typroa 之类的编辑器，甚至是专业的代码编辑器请自行研究。

# 3.2 文件一站式管理
VSCODE 可以很方便地对网站进行管理：

克隆完成后，通过快捷方式 `Ctrl+K Ctrl+O` 或者菜单 `File（文件）》Open Folder（打开文件夹）` 打开刚克隆完的仓库目录。

![打开文件夹](https://cdn.jsdelivr.net/gh/828767/static/images/vscode_markdown_editor.png)

也可以直接调出命令行终端：

启动 `vscode` ，通过快捷 `CTRL+~` 或者菜单 `Terminal》New Terminal（新建终端）`

![新建终端](https://cdn.jsdelivr.net/gh/828767/static/images/vscode_new_terminal.png)
	
至此，我们就可以在 `vscode` 中便捷地增删改网站源文件了。


# 3.3 界面化Git操作
VSCODE 很好地集成了Git操作，在我们增删改文件后，可以直接在编辑器界面与 Git 仓库提交同步：
![Git操作界面概览](https://cdn.jsdelivr.net/gh/828767/static/images/vscode-git.png)

提交只是本地操作，要同步到外网，还需要进一步 **推送或同步** ，就是点 VSCODE 左下角那个循环图标 。如果想一次性完成提交和推送，可以在填写完变更信息后，点击提交右侧的下拉按钮选择提交并推送。

![Git提交并推送](https://cdn.jsdelivr.net/gh/828767/static/images/vscode-git-push.png)

VSCODE 界面上其他按钮功能可以将鼠标移动到对应图形上方悬停一下，然后就会有功能提示了，请自行查阅并使用。基本的演示如动图：

![简单的Git提交演示](https://cdn.jsdelivr.net/gh/828767/static/images/vscode-git-commit.gif)

直接填写变更说明提交表示把所有变更提交，如果只想提交指定某个文件，那么如上图所示，点击变更文件后面的 `＋` 单独暂存变更并提交，其他未暂存变更的文件不会被提交。

第一次使用时会提示是否直接提交等提示，请正确选择是，允许等。同时，推送到仓库需要授权，如果是 `SSH` 仓库地址，请正确配置 SSH 秘钥。

更多操作建议去学习下 Git 基础知识，可求助我们的战略合作伙伴 Google 和百度。

虽然项目仓库主页直接增删改文件都可以，但网页上只能一个一个文件操作，建议还是同步到本地使用，借助编辑器事半功倍，也相当于多了个源码本地备份。

# 3.4 MarkDown 插件
作为 MarkDown 编辑器和文件管理器，建议安装以下插件：
1. Git History
2. GitLens supercharges
3. Markdown All in One
4. Markdown Preview Mermaid Support
5. Markdown Table
6. Markdown Shortcuts

其他有用的插件请自行探索。