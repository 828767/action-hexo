---
title: '从零开始建个小站'
categories:
  - 做网站
tags:
  - 教程
date: 2022-05-01 11:22:33
updated: 2022-05-01 11:22:33
toc: true
comments: true
keywords: ""
description: "虽然有微信朋友圈，QQ空间，微博等可以记录点点滴滴，但他们要么是没法扩大圈子，要么是加以各种限制，到头来这些数据产权还都属于马家，更不用谈某天实现增值获取收益，寄人篱下终究不如自己做主：建个自己掌控的网站！"
top:
---

# 前置知识

## 引言
互联网时代，大家都想在浩瀚的网络世界留下点印记。

虽然有微信朋友圈，QQ空间，微博等可以记录点点滴滴，但他们要么是没法扩大圈子，要么是加以各种限制，到头来这些数据产权还都属于马家，更不用谈某天实现增值获取收益，寄人篱下终究不如自己做主：建个自己掌控的网站！

本文便旨在试图引导小白从零开始，免费或者低成本建个自己的小站。

## 建站须知
1. 虽然说是零基础建站，但一些互联网及计算机基本知识技能还是不能少的，如怎么安装软件，怎么敲命令，怎么解析域名……看不懂不想看等还是安心去发朋友圈吧
2. 建站就需要文件托管服务，如上传到GitHub仓库，自己买的云服务器，虚拟主机等
3. 网站对外需要有IP或者域名（一般都不会直接IP对外服务），所以要么用GitHub提供免费的二级域名，要么自行购买域名并解析到文件托管服务器
4. 建站时会涉及各种配置设置，而且各程序，各主题都不尽相同，都需要根据实际对象依照文档进行配置，所以需要具备阅读文档的能力

## 基本概念

| 名词          | 解释说明                                               |
| ------------- | ------------------------------------------------------ |
| git           | 大名鼎鼎的分布式版本管理工具，每个版本改了什么一目了然 |
| GitHub        | 版本管理托管商，全球最大的男性交友社区                 |
| action        | GitHub提供的在线执行环境，类似于一个虚拟机             |
| pages         | GitHub提供的网页托管访问服务，每用户一个免费二级域名   |
| npm           | 依赖包管理工具，各种套娃                               |
| MarkDown      | 轻量标记语言，写文档必备技能                           |
| 服务器/云主机 | 存放文件24小时在线提供网络访问服务的计算机             |
| 域名          | 互联网上便于人类识别记忆的访问地址                     |
| ICP备案       | 大陆境内服务器需要，有问题方便FBI请喝茶或上门送温暖    |
| 主题/模板     | 套用后实现展现相应的界面外观及功能                       |

## 网站程序选型

网站程序选型主要依据环境依赖程度和维护难度，以及网络上免费资源可持续性考虑，对大多数普通用户，建议选择主流程序：
- 首选 `hugo/hexo`：HTML静态页渲染框架，速度快，可免费托管到GitHub仓库，MarkDown文档维护，主题多可满足大部分需求。
- 其次 `WordPress/typecho`：几乎没有免费资源可用，需自备服务器，但有后台界面，网络上插件多，文档教程多

市面上网站程序比较多，罗列了几个比较主流的框架，更多可以自行通过搜索引擎查找对应文档。

| 程序框架  | 环境依赖          | 维护难度 | 推荐度     | 常见用途                               |
| --------- | ----------------- | -------- | ---------- | -------------------------------------- |
| hugo      | /                 | ★       | ★★★★★ | 个人网站，企业官网，在线文档，求职简历 |
| hexo      | nodejs            | ★★     | ★★★★☆ | 个人网站，企业官网，在线文档，求职简历 |
| gitbook   | nodejs            | ★★★   | ★★       | 在线文档                               |
| vuepress  | nodejs            | ★★     | ★★★     | 个人网站，在线文档                     |
| docsy     | nodejs            | ★★★   | ★★★     | 在线文档                               |
| WordPress | MySQL，PHP        | ★★     | ★★★★   | 个人网站，企业官网                     |
| Typecho   | MySQL，PHP        | ★★☆   | ★★★☆   | 个人网站，企业官网                     |
| Zblog     | MySQL/SQLite，PHP | ★★     | ★★★     | 个人网站，企业官网                     |

> PS：维护难度和推荐度都是主观意见，推荐度高主要是基于部署简单，可选主题多，互联网免费资源多，对最终实现的功能需求未做考虑，大部分情况根据自己实际需求考量。

# 建站方案选择
既然这是篇小白零基础建站教程，那么就不会涉及带门槛的方案，只是简单罗列了适合新手的案例，其他同等方案或者更复杂方案等熟悉了可以再自行研究。

## 方案对比
1. 免费：**hugo/hexo + GitHub + GitHub免费二级域名/自备域名**
   
   ```mermaid
    flowchart LR;
      本地维护MarkDown内容 -- hugo/hexo渲染 -->本地效果预览
      GitHub私有仓库 -- 绑定自备域名 --> 公开pages服务
      本地维护MarkDown内容 <-- git同步 --> GitHub私有仓库 -- 触发action自动渲染 --> 公开pages服务
   ```

   - 优点：有免费资源，静态页速度快，网站源文件通过git版本管理安全可靠
   - 缺点：需要点MarkDown语法知识，缺稳妥的界面化管理后台


2. 付费：**WordPress/Typecho/Zblog + 自备服务器 + 自备域名**
   
   ```mermaid
    flowchart LR;
      自备域名 -- DNS解析 --> 自备服务器 --> 网站对外服务
      网站界面后台维护内容 --> 自备服务器 -- 大陆区服务器 --> ICP备案 --> 网站对外服务
   ```

   - 优点：功能强大几乎能满足所有需求，装好后带后台，纯界面操作无门槛
   - 缺点：需要自己购买服务器和域名，对服务器要求高，响应速度相对慢点


## 准备条件
### 免费方案：
  ```mermaid
  flowchart TB;
  免费方案 --必须--> 注册GitHub账号 & 安装Git客户端
  注册GitHub账号 --> 创建仓库 & 配置访问令牌
  安装Git客户端 --编辑MarkDown源码--> 发布到GitHub
  免费方案 --可选--> 安装本地环境 & 装个趁手的编辑器 & 购买域名
  装个趁手的编辑器
  ```

  1. **GitHub账号**：要使用免费的资源，不得注册个账号绑定才能找得到么？虽然国内Gitee也有，但绑定自己的域名要收费，而且内容要审核，所以还是直接用GitHub吧。当然，你有自己服务器和域名也可以用来替代。
  2. **Git客户端**：用来同步管理源代码，改了什么一目了然
  3. **MarkDown 编辑器**：纯手工敲代码是不可能的，借助编辑器事半功倍，而且还能和Git结合，大大降低难度
  4. **域名「可选」**：花点小钱占个自己的域名赏心悦目，也好打响自己的品牌，万一哪天走了张[伟波](/ "微博在2010年耗资800万收购 weibo.com")的运呢？


### 付费方案：
  ```mermaid
  flowchart LR;
  付费方案 --必须--> 购买域名 & 购买服务器
  购买服务器 --大陆区服务器--> ICP备案
  购买服务器 --> 安装环境并部署网站 & 后台发布内容
  ```

  1. **域名**：虽然也有免费的，但还是建议花钱买，每年几十元
  2. **服务器/云主机/虚拟主机**：需要带数据库，支持PHP及安装扩展
  3. **ICP备案**：如果用大陆区服务器，必须先工信部ICP备案后才可用，大约需耗时6周

<!-- <script type="text/javascript" async
  src="https://cdn.staticfile.org/mermaid/9.1.1/mermaid.min.js">
</script> -->


# 环境准备
如果你选择的是自备服务器的付费方案，那么直接在服务器上安装环境部署网站程序即可，本文不做详细介绍，下文只针对免费方案进行详细说明。

## 本地 Git 设置

### 安装Git
到 [Git官网](https://git-scm.com/downloads) 下载自己操作系统对应的安装包或者按对应命令安装即可。

<details><summary>Windows</summary>

安装的时候一路选默认 `next` 到底就行，最后会在文件夹右键菜单中出现 `Git Bash Here` 方便使用。

![Git右键菜单](https://cdn.jsdelivr.net/gh/828767/static/images/git_menu_gitbashhere.png)

</details>
<details open><summary>macOS</summary>

Install [homebrew](https://brew.sh/) if you don't already have it, then:

```
brew install git
```

</details>
<details><summary>Linux</summary>

**Debian/Ubuntu**
For the latest stable version for your release of Debian/Ubuntu
```
apt install git
```

**CentOS/Fedora**
```
yum install git
```

</details>

### 配置Git
如前一步图示，随便在哪个文件夹里：点 `右键` 菜单》点击 `Git Bash Here` 》启动 `Git Bash` 「macOS/Linux系统打开 `Terminal（终端）`」，复制粘贴如下命令：

```
# 设置Git用户信息
git config --global user.name "Your_Name"
git config --global user.email "Your_Email"
```
**注意**：请将命令中邮箱及用户名替换为自己实际信息

<details><summary>SSH密钥认证方式点此展开查看生成密钥对方法</summary>

相对于前文提到的 [PAT](#添加-personal-access-token "Personal access token")，使用 SSH 密钥是另一种更安全的方式。

<div style="padding: 15px; border: 1px solid transparent; border-color: transparent; margin-bottom: 20px; border-radius: 4px; color: #8a6d3b;; background-color: #fcf8e3; border-color: #faebcc;">
<strong>注意：</strong> 
<p>2021年8月14号开始，GitHub弃用账密验证Git操作，改用token或SSH密钥</p>
<p>GitHub 在 2022 年 3 月 15 日通过删除较旧的不安全密钥类型提高了安全性，不再支持 DSA 密钥 (<code>ssh-dss</code>)。</p>
<p>在 2021 年 11 月 2 日之前 <code>valid_after</code> 的 RSA 密钥 (<code>ssh-rsa</code>) 可以继续使用任何签名算法。 在该日期之后生成的 RSA 密钥必须使用 SHA-2 签名算法。 某些较旧的客户端可能需要升级才能使用 SHA-2 签名。</p></div>

当前就相当于强制用户使用超长随机串密码，安全加强是好事，遵循规则使用 `SHA-2` 签名规则密钥即可：

```
# 生成密钥对，一路回车默认即可
# 如已有其他密钥对在用，自己改下生成的文件名以防覆盖
ssh-keygen -t ed25519 -C "Your_Email"
```

如果您使用的是不支持 `ed25519` 算法的旧系统，请使用：
```
ssh-keygen -t rsa -b 4096 -C "Your_Email"
```
更多密钥相关详细信息可参阅 [GitHub官方文档][new-SSH-key]

如果你是一路回车生成密钥对，那么生成的密钥对会保存在：`~/.ssh/` 目录下，`~` 表示用户目录，如操作系统登录用户名是 `xyz` ，那么在Windows下路径则为 `C:\Users\xyz\.ssh` ,macOS/Linux下路径为 `/home/xyz/.ssh` ，其中：
```
~/.ssh/id_ed25519 //私钥，保存在本地
~/.ssh/id_ed25519.pub //公钥，配置到远端
```

到此，本地Git环境已准备妥当，下一步将公钥配置到GitHub中就能使用了。

</details>

## GitHub 设置

### 注册GitHub账号
如果已有账号则跳过此步骤，直接登录设置即可。如果还没有账号，请访问 https://github.com ，完成注册和邮箱认证，一般用户选择免费套餐就足够用了：

![免费套餐额度](https://cdn.jsdelivr.net/gh/828767/static/images/github.com_join_recommended_plan.png)

<details open><summary>个人访问令牌认证方式</summary>

### 配置 `Personal access token`
取消了用户密码认证后，`PAT`「`Personal access token`」成了 GitHub 官方默认的HTTPS认证方式，比SSH密钥安全性差点，但配置简单点。

1. 登录后，在任何页面的右上角，单击右上角个人资料照片，然后单击 `Settings（设置）`
2. 在左侧栏中，单击  `<>开发者设置`》`Personal access tokens（个人访问令牌）`

    ![Personal access tokens](https://docs.github.com/assets/cb-7169/images/help/settings/personal_access_tokens_tab.png)

3. 单击 `Generate new token（生成新令牌）`，如需密码验证输密码验证即可。

    `Note` 行里随便填，写给自己看的，过期时间建议选择 `No Expiration（永不过期）`

    ![Generate new token](https://cdn.jsdelivr.net/gh/828767/static/images/personal_access_token.png)

    <div style="padding: 15px; border: 1px solid transparent; border-color: transparent; margin-bottom: 20px; border-radius: 4px; color: #8a6d3b;; background-color: #fcf8e3; border-color: #faebcc;">作为安全防范措施，GitHub 会自动删除一年内未使用的个人访问令牌。 </div>

4. 如下勾选相关权限
   
    ![repo](https://cdn.jsdelivr.net/gh/828767/static/images/personal_access_token_scopes.png)    
    ![admin/user](https://cdn.jsdelivr.net/gh/828767/static/images/personal_access_token_scopes1.png)

5. 最后点击 `Generate token` 生成个人访问令牌。

    ![Generate token](https://docs.github.com/assets/cb-10912/images/help/settings/generate_token.png)

添加完成后，会显示刚添加的令牌，该令牌明文只会显示一次，所以请 <font color=red>务必复制保存下来备用</font>否则就需要删除重新生成，后面项目仓库和本地访问认证都能用得到该令牌。

![令牌明文内容](https://cdn.jsdelivr.net/gh/828767/static/images/personal_access_tokens.png)

</details>
<details><summary>SSH密钥认证方式点此展开查看配置方法</summary>

### 配置密钥

为了使用方便，给GitHub添加一个用户密钥，一个密钥可作用于整个账号的增删改查操作。

1. 将 SSH 公钥内容复制到剪贴板「假设都按前面的默认操作」
    <details open><summary>Windows</summary>

    打开 `Git Bash` ，复制粘贴如下命令
    ```
    clip < ~/.ssh/id_ed25519.pub
    //该命令自动将公钥存到剪贴板，直接用文本编辑器打开公钥再复制也是一样的
    ```

    </details>
    <details><summary>macOS/Linux</summary>

    打开 Terminal（终端），复制粘贴如下命令：
    ```
    cat ~/.ssh/id_ed25519.pub
    // 执行完将打印出来的公钥内容完整复制待用
    ```

    </details>

2.  登录GitHub账号后，在任何页面的右上角，单击右上角个人资料照片，然后单击弹出下拉中的 `Settings（设置）`

3. 选择左侧 `Access`》 点击 `SSH and GPG keys`，点击 `New SSH key（新 SSH 密钥）`
    
    ![Add New SSH key](https://cdn.jsdelivr.net/gh/828767/static/images/github_set_access_new_ssh.png)

4. 在 `Title`（标题）字段中，为新密钥添加描述性标签便于识别用途。 例如，如果您使用在个人Mac上，此密钥名称可能是 `Personal MacBook`。

5. 将前面复制的公钥串粘贴到 `Key`（密钥）字段
    
    ![粘贴公钥串](https://docs.github.com/assets/cb-24796/images/help/settings/ssh-key-paste.png)

6. 最后点击 `Add SSH key（添加 SSH 密钥）` 完成添加

</details>

# 开始使用
## 建站实操
本实操仅针对 [建站方案](#建站方案选择) 中提及的免费方案：**hugo/hexo + GitHub + GitHub免费二级域名/自备域名**，另外的付费方案自带网站后台，界面化的一体操作没什么好演示的，如有需要可求助我们的战略合作伙伴Google和百度。

### 建立存储仓库
虽然可以通过分支控制源文件和对外访问文件，但还是建议分仓库存储：
1. **公开：GitHubPages仓库**：页面文件对外访问
2. **私有：项目仓库**：存储网站源文件，只有自己可见防止提交记录、网站配置等机密信息外泄

#### **公开：GitHubPages仓库**
1. 登录GitHub，在任何页面的右上角，使用 `+` 下拉菜单选择 `New repository（新建仓库）`
    
    ![新建GitHubPages仓库](https://docs.github.com/assets/cb-11427/images/help/repository/repo-create.png)

2. 因为要对外访问，所以名称必须为：`<owner>.github.io`，且可见性必须为 `public(公开)`：
    
    ![username.github.io](https://docs.github.com/assets/cb-34195/images/help/pages/create-repository-name-pages.png)
    ![可见性选public(公开)](https://docs.github.com/assets/cb-20877/images/help/repository/create-repository-public-private.png)

3. 此时只是个空仓库备用，等有提交了再来设置pages
   
#### **私有：项目仓库**
项目仓库保存着网站的源代码，控制网站的输出内容和页面样式。这里用导入模板仓库的方法，快速生成具有与模板仓库相同的目录结构和文件的新仓库，该模板仓库实现功能：
- 自动将源文件渲染并发布到GitHubPages仓库pages分支
- 自动判断配置的网站域名，并决定是否需要绑定 `CNAME`
- 自动渲染发布到当前项目仓库pages分支，如果不设置为私有仓库可作为项目主页访问
- pages分支只保留最后1次提交记录

1. 打开[这个模板仓库](https://github.com/828767/action-hugo "hugo框架模板")主页面
2. 在文件列表上方，单击 `Use this template（使用此模板）`
    
    ![使用模板](https://docs.github.com/assets/cb-36544/images/help/repository/use-this-template-button.png)

3. 输入你想要的仓库名称和描述（可选），网站源码仓库可见性建议选择 `Private（私有）`

    ![项目仓库名称](https://docs.github.com/assets/cb-25139/images/help/repository/create-repository-name.png)

4. （可选）要包括模板中所有分支的目录结构和文件，而不仅仅是默认分支，请勾选 `Include all branches（包括所有分支）`
5. 最后点击 `Create repository from template（从模板创建仓库）`

截止当前，我们已经准备好了建站需要的存储仓库，接着还需要配置相应的权限才能顺利对外发布。

### 配置发布令牌

还记得 GitHub 设置中配置的 `Personal access token` 么，前面叮嘱复制保存下来，下面该派上用场了：

1. 导航到刚创建的项目仓库主页面，在仓库名称下，单击  `Settings（设置）`
   
    ![Settings（设置）](https://docs.github.com/assets/cb-21851/images/help/repository/repo-actions-settings.png)
    
2. 点击左侧的 `Secrets》Actions`，新建仓库秘钥

    ![新建仓库秘钥](https://cdn.jsdelivr.net/gh/828767/static/images/repo_set_repo_secret.png)

3. 在 `Name（名称）`输入框中键入秘钥的名称必须为：`ACTION_ACCESS_TOKEN` ，`Value` 框粘贴之前复制保存的那串值
    
    ![ADD ACTION_ACCESS_TOKEN](https://cdn.jsdelivr.net/gh/828767/static/images/repo_set_repo_secret1.png)

4. 最后单击 `Add secret（添加秘钥）` 保存完成

    ![ACTION_ACCESS_TOKEN](https://cdn.jsdelivr.net/gh/828767/static/images/repo_set_repo_secret2.png)

### 小试牛刀
经过之前的一番操作，服务器上一切都准备就绪了，可以试试好使与否，直接在项目仓库中触发个提交就行，比如点击 `config.toml` 或 `config.yml` 编辑里面的url，然后保存提交。

![提交变更试效果](https://cdn.jsdelivr.net/gh/828767/static/images/github_commit_first.png)

项目仓库提交变更后，要不了一分钟会自动将源文件渲染并发布到pages仓库，到pages仓库中可见刚从项目仓库提交过来的分支，要对外访问则要设置为pages指定分支。

![自动提交的分支](https://cdn.jsdelivr.net/gh/828767/static/images/github_repo_new_branch.png)

### 设置pages分支
前文已经提到pages分支了，用户pages仓库为：`<owner>.github.io`，其他则为项目仓库，设置方法都是一样的：

1. 导航到pages仓库主页，点击 `Settings（设置）`，点击左侧 `Pages` 标签，选择对应的分支

    ![Pages-branch](https://cdn.jsdelivr.net/gh/828767/static/images/githubpages_select_branch.png)

2. 点击保存后，大约5分钟，就可以通过页面上提示的地址对外访问了。
    
    ![<owner>.github.io](https://docs.github.com/assets/cb-27618/images/help/pages/click-pages-url-to-preview.png)

## 本地维护

工欲善其事必先利其器，虽然没后台，选用个好用的编辑器后甚至比WordPress之类的后台还方便。

### 文档编辑器
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

**作为Hugo/Hexo管理器，还可以安装其对应扩展，具体自己去搜索安装**。

其他更多扩展根据自己需求去发觉安装，代码美化，自动填充，自动关闭标签等功能应有尽有。

### 克隆仓库到本地
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

### 安装本地环境
如果你想在本地就直接看到渲染后的效果，那么还需要安装个本地环境。
<details open><summary>Hugo</summary>

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

</details>
<details><summary>Hexo</summary>

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

</details>


## 个性设置
项目仓库克隆下来，网站的各项设置都是默认的，一些标题，作者之类的需要根据自己的实际情况进行修改，个性设置主要是网站根目录的框架配置和主题配置。好在 `hugo` 和 `hexo` 配置结构大同小异，而且都支持将配置文件放在网站根目录下，只需要修改配置，今后主题更新只需要同步配置其他也互不影响。

> **每套用一个主题，渲染出来的网站界面和功能都有所不同，所以除了基础配置，各个主题设计的配置项都可能不一样，所以一定要依照主题模板文档去配置！！！**

> **一定要依照主题模板文档去配置！！！**

> **一定要依照主题模板文档去配置！！！**


<details open><summary>Hugo</summary>

Hugo只有一个配置文件，默认的配置功能非常少，只包含网站标题，主页地址和语言，其他功能都依赖主题模板实现。

主题到 [官网主题页][Hugo主题] 去选自己喜欢的，然后依照主题文档去操作，这就是前面要强调三遍的**依照主题文档去配置！**

![Hugo官网主题页](https://cdn.jsdelivr.net/gh/828767/static/images/hugo-themes.png)

**以 `Ananke` 主题为例：**
1. 在 [官网主题页][Hugo主题] 点击 `Ananke` 主题预览图或标题后，会被导航到主题说明页：https://themes.gohugo.io/themes/gohugo-theme-ananke/
2. 该页面有主题预览及功能说明等，当然也包括该主题怎么安装，怎么配置，以下也就是搬运主题文档演示一遍
3. 按文档说明安装该主题:
    ```
    git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
    # 作为子模块安装到themes/ananke，后期项目仓库部署时会从主题仓库更新
    ```
4. 配置 `config.toml`，以下仅是演示，详细规则可参阅 [Hugo官方配置说明][hugo-config]
    
    在主题目录下有个 `exampleSite` 文件夹，相当于就是一个完整的站点演示了，直接把该目录下的 `config.toml` 复制替换到项目仓库根目录下，或者复制里面的内容移到已有的 `config.toml` 里也是一样的，最后配置出来是这样的：
    ```
      title = "网站标题"
      baseURL = "https://yiwangmeng.cn"
      uglyurls = true # true or false, 'Pretty URLs' VS 'Ugly URLs': https://gohugo.io/content-management/urls/#pretty-urls
      languageCode = "zh-cn" # "en-us" default
      theme = "ananke"  # 指定主题
      resourceDir = "../resources"

      DefaultContentLanguage = "zh" # 默认展示语言，和[languages]配置对应
      SectionPagesMenu = "main"
      Paginate = 9 # this is set low for demonstrating with dummy content. Set to a higher number
      googleAnalytics = "
      enableRobotsTXT = true

      [languages]
        [languages.zh]
          title = "Ananke"
          weight = 1
          contentDir = "content/zh" # 该语言内容存贮目录
          # languageDirection = 'rtl' for Right-To-Left languages
        [languages.en]
          title = "Ananke English"
          weight = 2
          contentDir = "content/en"

      [sitemap]
        changefreq = "monthly"
        priority = 0.5
        filename = "sitemap.xml"

      [params]
        text_color = ""
        author = ""
        favicon = ""
        site_logo = ""
        description = "The last theme you'll ever need. Maybe."
        # choose a background color from any on this page: http://tachyons.io/docs/themes/skins/ and preface it with "bg-"
        background_color_class = "bg-purple"
        recent_posts_number = 3

      [[params.ananke_socials]]
      name = "twitter"
      url = "https://twitter.com/GoHugoIO"
    ```
5. 填充内容

    直接把主题 `exampleSite` 的 `static` 和 `content` 拷贝到项目网站根目录，然后启动本地环境预览下： `hugo server` ，除了自己修改过的个性化信息，其他跟主题演示没区别，然后依葫芦画瓢修改或者新增自己要的内容就可以了，关键还是要依照主题文档操作！


</details>
<details><summary>Hexo</summary>

和Hugo一样，Hexo内容个性化也是靠配置文件完成，展示个性化根据主题而定。Hexo主题可以到 [官网主题页][Hexo主题] 去挑选：

![Hexo官网主题页](https://cdn.jsdelivr.net/gh/828767/static/images/hexo-themes.png)

配置文件包含根目录下的 `_config.yml` 和主题目录下的 `_config.yml` ，在新版中这俩配置可以合而为一，也可以将主题目录下的 `_config.yml` 复制到根目录下命名为： `_config.主题名称.yml` ，如  `_config.maupassant.yml` 表示主题 `maupassant` 的配置，详见 [Hexo主题配置说明][Hexo主题配置]。

配置优先级为：项目网站根目录下的 `_config.yml` 》 `_config.maupassant.yml` 》主题目录下的 `_config.yml` ，**建议使用 `_config.主题名称.yml` 方式存储主题配置**。

Hexo和Hugo一样，基础配置较少，剩下的**请参照主题文档配置！请参照主题文档配置！请参照主题文档配置！**

</details>

## 内容增/删/改

- 增：新增文章、页面、图片等
- 删：删除文章、页面、图片等
- 改：对已有的文章、页面等进行修改

**所有的增删改都需要提交到线上仓库才能看到改变**。使用本站提供的项目仓库，提交源代码后，会自动触发渲染发布，然后静态上端网络缓存更新后才能看到最新结果。

### 注意格式
不管是Hugo还是Hexo，他们都只是一种渲染框架，所以MarkDown源代码都需要特定的 `Front-matter` 标记，也就是两行 `---` 中间的那段。
```
---
title: '网页模板 pug 基本语法'
categories:
  - 学编程
tags:
  - 博客建站
date: 2021-12-10 15:22:57
updated: 2021-12-10 15:22:51
toc: true
comments: true
keywords: ''
description: 'pug原名jade，因版权问题更名为pug，即哈巴狗。与hexo默认模块ejs一样，pug也是一个模板引擎，可用于快速的网站开发，当然也可以用于静态博客网站的设计。本站点现时所用主题manupassant也使用了pug。'
top:
---
```
以上 `Front-matter` 是 Hexo 程序的，其中设置项也需要对应的主题支持，如果不是 Hexo 基础 `Front-matter` ，具体需要添加什么根据主题文档来。

`Front-matter` 基础配置项可见：
1. [Hugo-Front-Matter][]
2. [Hexo-Front-matter][]

### 实例演示
<details open><summary>Hugo</summary>



</details>
<details><summary>Hexo</summary>



</details>


## MarkDown 语法
### 📌 **Titles**

- Heading 1: `# A first-level title`
- Heading 2: `## A second-level title`
- Heading 3: `### A third-level title`


### 💻 **Code blocks**
`creates a new code block.`，源码如下：
```
`creates a new code block.`
```

\````py⏎` creates a new code block with Python syntax highlighting.


### **📋** **Lists**

We automatically detect ordered and un-ordered lists as you type. 

Begin a line with `- ` or `* ` to start a bullet list.  
Being a line with `1. ` to start a numbered list. Use `Tab` to go one level deeper, and `Shift+Tab` to go up. Begin a line with `- [ ] ` to start a task list.


### **🎤** **Quotes**

Begin a line with `> ` to create a block quote.

### **🐮** **emoji markup**
😊 	_😃_ 	😴

[Complete list of github markdown emoji markup](https://gist.github.com/rxaviers/7360908)

### References

1. [Markdown 入门参考](http://xianbai.me/learn-md/article/about/readme.html)
2. [Markdown 基本语法](https://markdown.com.cn/basic-syntax/)
3. [Markdown 菜鸟教程](https://www.runoob.com/markdown/md-tutorial.html)




[new-SSH-key]: https://docs.github.com/cn/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent "生成密钥对"

[add-SSH-to-GitHub]: https://docs.github.com/cn/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account "新增 SSH 密钥到 GitHub 帐户"

[hogo-install]: https://gohugo.io/getting-started/installing/ "Hugo官方安装文档"
[hugo-config]: https://gohugo.io/getting-started/configuration/ "Hugo官方配置说明"
[Hugo主题]: https://themes.gohugo.io/ "Hugo官方主题展示页"
[Hexo主题]: https://hexo.io/themes/ "Hexo官方主题展示页"
[Hexo主题配置]: https://hexo.io/zh-cn/docs/configuration#%E4%BD%BF%E7%94%A8%E4%BB%A3%E6%9B%BF%E4%B8%BB%E9%A2%98%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6 "使用代替主题配置文件"

[Hexo-Front-matter]: https://hexo.io/zh-cn/docs/front-matter
[Hugo-Front-Matter]: https://gohugo.io/content-management/front-matter/ "Front Matter Formats"