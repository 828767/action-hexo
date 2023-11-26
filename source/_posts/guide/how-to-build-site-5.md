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
VSCODE 就是个不错的选择，自行到 [微软官方网站](https://code.visualstudio.com/download) 去下载安装。
> 如果墙内下载慢，可把下载地址中 `az764295.vo.msecnd.net`  改为 `vscode.cdn.azure.cn` 可实现秒下，如:
> 
> Windows版墙内地址：https://vscode.cdn.azure.cn/stable/ee2b180d582a7f601fa6ecfdad8d9fd269ab1884/VSCodeSetup-x64-1.76.2.exe
>
> macOS版墙内地址：https://vscode.cdn.azure.cn/stable/ee2b180d582a7f601fa6ecfdad8d9fd269ab1884/VSCode-darwin-universal.zip

![VSCODE](https://static.yiwangmeng.com/https://raw.githubusercontent.com/828767/static/master/images/vscode-hexo.png)

VSCODE 是当前最流行的编辑器，免费开源，专业和业余都能胜任：
1. 全目录管理，一个界面可以管理整个目录下的文件
2. 语法格式显示，也能实时预览
3. 与Git集成，可以界面化操作Git提交同步，比较等
4. 集成命令终端，预览调试方便


VSCODE 可以在当前界面直接调出命令行终端，方便输入命令使用：

启动 `VSCODE` ，Windows 版可以通过快捷 `CTRL+~` 或者菜单 `Terminal》New Terminal（新建终端）`

![新建终端](https://static.yiwangmeng.com/https://raw.githubusercontent.com/828767/static/master/images/vscode_new_terminal.png)

该终端默认使用系统终端，功能上有些许差异，建议设置默认终端为 `Git Bash`，方法：点击终端窗口右上角 ➕ 右侧的 `下拉箭头`

![设置默认终端](https://static.yiwangmeng.com/https://raw.githubusercontent.com/828767/static/master/images/vscode-set-terminal-defalt.png)
![选择Git Bash](https://static.yiwangmeng.com/https://raw.githubusercontent.com/828767/static/master/images/vscode-set-terminal-git.png)

> Windows 11 系统上，不知道什么原因系统变量可能会失效，导致无法运行 `npm` 或者 `hexo` 命令，那么请直接使用 `Git Bash Here` 终端即可，或者自己去添加对应系统变量解决。

其他如 Atom、Sublime Text、Typroa 之类的编辑器也都可以，甚至是专业的代码编辑器请自行研究。

# 3.2 文件一站式管理
VSCODE 可以很方便地对网站进行管理：

克隆完成后，通过快捷方式 `Ctrl+K Ctrl+O` 或者菜单 `File（文件）》Open Folder（打开文件夹）` 打开刚克隆完的仓库目录。

![打开文件夹](https://static.yiwangmeng.com/https://raw.githubusercontent.com/828767/static/master/images/vscode_markdown_editor.png)
	
至此，我们就可以在 `vscode` 中便捷地增删改网站源文件了。

> 文件修改后，请`记得要保存`，`记得要保存`，`记得要保存`，保存文件的快捷键：`Ctrl+S`

# 3.3 界面化Git操作
VSCODE 很好地集成了Git操作，在我们增删改文件后，可以直接在编辑器界面与 Git 仓库提交同步：
![Git操作界面概览](https://static.yiwangmeng.com/https://raw.githubusercontent.com/828767/static/master/images/vscode-git.png)

> 点 `commit` 前请务必填写 `message` ，告知后来人改了什么，为什么会有这次变更，这是 Git 版本管理基本规范

提交只是本地操作，要同步到外网，还需要进一步 **推送或同步** ，界面上有好几处 `同步` 、`push` 等功能按钮，或者直接点 VSCODE 窗口左下角状态栏上 🔄 即可完成Git数据同步。

![Git同步状态](https://static.yiwangmeng.com/https://raw.githubusercontent.com/828767/static/master/images/github-sync.png)

> 上图中 `🔄 0↓ 1↑` 表示有 0 个变更待拉取/下载，有 1 个变更待推送/上传

如果想一次性完成提交和推送，可以在填写完变更信息后，点击提交右侧的下拉按钮选择提交并推送。

![Git提交并推送](https://static.yiwangmeng.com/https://raw.githubusercontent.com/828767/static/master/images/vscode-git-push.png)

VSCODE 界面上其他按钮功能可以将鼠标移动到对应图形上方悬停一下，然后就会有功能提示了，请自行查阅并使用。基本的演示如动图：

![简单的Git提交演示](https://static.yiwangmeng.com/https://raw.githubusercontent.com/828767/static/master/images/vscode-git-commit.gif)

直接填写变更说明提交表示把所有变更提交，如果只想提交指定某个文件，那么如上图所示，点击变更文件后面的 `＋` 单独暂存变更并提交，其他未暂存变更的文件不会被提交。

第一次使用时会提示是否直接提交等提示，请正确选择是、总是、允许……等。
> 推送到仓库需要授权，如果是 `SSH` 协议仓库地址，还需要先正确配置 `SSH` 密钥，方法请见 {% post_link guide-how-to-build-site-4 %} 中相关章节。

更多操作建议去学习下 Git 基础知识，可求助我们的战略合作伙伴 Google 和百度。

虽然项目仓库主页直接增删改文件都可以，但网页上只能一个一个文件操作，建议还是同步到本地使用，借助编辑器事半功倍，也相当于多了个源码本地备份。

# 3.4 推荐插件
作为 MarkDown 编辑器和文件管理器，建议安装以下插件：
1. `Git History`：界面化查看及管理 Git 提交记录
2. `GitLens supercharges`：在文件内容中提示 Git 变更异同等信息
3. `Markdown All in One`：MarkDown 预览及一些快捷方式
4. `Markdown Preview Mermaid Support`：MarkDown 流程图、时序图等渲染支持
5. `Markdown Table`：快速插入 MarkDown 表格或者转换成表格代码
6. `Markdown Shortcuts`：MarkDown 各种语法快捷方式

其他有用的插件请自行探索。