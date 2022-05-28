---
title: '从零开始建个小站 - 实操：代码拉到本地'
date: 2022-05-28 20:20:20
categories:
  - 做网站
tags:
  - 教程
---
工欲善其事必先利其器，Hexo/Hugo虽然没后台，选用个好用的编辑器后甚至比WordPress之类的后台还方便。

## 文档编辑器
优秀的MarkDown编辑器不少，Typora、Atom、vscode等都是其中的佼佼者，推荐 `vscode`：
- 微软主导开发，全平台开源免费
- 用户众多，各种功能插件一应俱全
- 支持目录树管理，所有文件操作都可以在一个界面内完成
- 支持分屏及实时预览
- 与Git终端集成，版本管理一目了然，支持 `pull` 与 `push` 等界面化操作

![vscode](https://user-images.githubusercontent.com/35271042/118224532-3842c400-b438-11eb-923d-a5f66fa6785a.png)

**作为 MarkDown 编辑器，推荐安装以下扩展**
1. Git History
2. GitLens supercharges
3. Markdown All in One
4. Markdown Preview Mermaid Support
5. Markdown Table
6. Markdown Shortcuts

其他更多扩展根据自己需求去发觉安装，代码美化，自动填充，自动关闭标签等功能应有尽有。

## 克隆仓库到本地
虽然项目仓库主页直接增删改文件都可以，但网页上只能一个一个文件操作，建议还是同步到本地使用，借助编辑器事半功倍，也相当于多了个源码本地备份。

前面已经准备好了 `vscode`，那么直接在 `vscode` 中操作。

1. 启动 `vscode` ，通过快捷 `CTRL+~` 或者菜单 `Terminal》New Terminal（新建终端）`

    ![新建终端](https://cdn.jsdelivr.net/gh/828767/static/images/vscode_new_terminal.png)

2. 在打开的终端中，通过 `git clone ` 命令将项目仓库克隆到本地「也可以安装 `GitHub Explorer` 像下载工具一样界面化操作」
    
    ```
    # 查看当前所处的目录，vscode打开文件夹后终端默认切到目录路径
    pwd
    # 为方便管理，切换到自己需要的目录，此示例是在D盘建了个git目录
    cd d:\git
    # 将仓库包括子项目保存到d:\git\REPOSITORY
    git clone --recurse-submodules https://github.com/USERNAME/REPOSITORY.git
    ```
    请将仓库地址换成实际地址，获取方法：打开仓库主页》在文件列表右上方有个 `Code` ，点击下拉复制，如下图所示：

    ![获取项目仓库地址](https://cdn.jsdelivr.net/gh/828767/static/images/github_clone_https_url.png)

3. 克隆完成后，通过快捷方式 `Ctrl+K Ctrl+O` 或者菜单 `File（文件）》Open Folder（打开文件夹）` 打开刚克隆完的仓库目录。

    ![打开文件夹](https://cdn.jsdelivr.net/gh/828767/static/images/vscode_markdown_editor.png)

至此，我们就可以在 `vscode` 中便捷地增删改网站源文件了。