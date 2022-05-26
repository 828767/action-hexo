---
title: 'GoodHexo仓库版使用简介'
toc: false
comments: true
categories:
tags:
keywords: ''
date: 2022-04-20 13:47:30
updated: 2022-04-20 13:47:30
top:    99
description: '这是一篇针对特定方案完工后的使用简介，其他更多更详细的细节教程请借助搜索引擎完成。

基于此方案，我们只需要维护 `MarkDown源文件仓库` ，每次提交源文件仓库后， 将自动触发 `Action` 完成渲染及部署工作。
'
---
![](../images/GoodHexo.png)
这是一篇针对特定方案完工后的使用简介，其他更多更详细的细节教程请借助搜索引擎完成。

基于此方案，我们只需要维护 `MarkDown源文件仓库` ，每次提交源文件仓库后， 将自动触发 `Action` 完成渲染及部署工作。

# 适用方案
MarkDown源文件仓库 → `Action` → `GitHub page` / 云服务器

# 使用步骤
## 1. 克隆仓库到本地
用GUI工具或者使用以下命令将 `MarkDown源文件仓库`  克隆到本地：
```
git clone 远程仓库地址 本地存放文件夹 --recursive
```
其中 `本地存放文件夹` 根据个人实际情况及喜好确定，比如 `D:\blogMarkDown` ， `--recursive` 参数会将包含的 `Git submodule 子模块` 一并克隆，本来就没有子模块管理的可以省略该参数。

## 2. 内容增/删/改
如果本地已经安装hexo，hugo等环境，那么使用对应的命令即可创建新文章，页面等。

如果本地不需要或者未安装这种环境，其实我们只需要复制一篇现成的文档，然后用编辑器修改即可，无非就是对应的 `Front-matter` 格式要保留，下面是个示例：

```yml
---
title: '这是个Hexo文章标题示例'  #文章标题，新建文章的时候填的会自动写到这里
date: 2018-1-12 17:19:27  #文章创建时间
categories: 搞软件 #分类，也可以如下一行那种换行后写分类
tags:  #标签
  - 晒酷软  #这是个标签
  - 做网站  #这是另一个标签
toc: true  #是否显示目录，false不显示，true显示，需要主题支持
top:  #填数字，值越大的文章在首页就越置顶，本包已集成
comments: true  #是否允许评论，需要主题支持
keywords: ''    #文章关键词，需要主题支持
description:  '文章摘要，可以是一大段，
可以换行，用英文引号括起来'  #不填则根据主题设计截取对应字数
---
上面部分是规定的头部信息，这行开始就是文章内容了...
```
> 注意：每一个参数的 : 或者 - 后，都需要至少留一个空格，如果不填值就无所谓，或者将参数行删除都行，就是不能不留空格直接写，否则会报错。


编辑器推荐用 [`vscode`](https://code.visualstudio.com/) 之类，切忌用Windows系统自带的记事本。举个栗子：
![hexo文章撰写示例](https://cdn.jsdelivr.net/gh/828767/static/images/hexo-edit.gif)

## 3. 提交到线上仓库
内容编辑完了，那就可以提交到线上仓库触发 `Action` 了，根据既定的 `Action` 规则，最终应该会完成渲染发布到指定的仓库或者服务器.

提交内容到仓库可以借助GUI工具，vscode 或者 github desktop 之类工具就没什么好说的了，也可以使用下方的命令：
```
git add --all
git commit -m "commit message"
git push
```

## 4. 查看结果
提交后要不了几分钟，等服务器刷新缓存，就能看到最终的 `Action` 结果了，对应的 `GitHub page` 仓库或者服务器上会有内容提交， `Action` 任务也有对应的详细运行日志，可自行到仓库中查看。

如果渲染成功，那对外的 `GitHub page` 网站上应该就有你更新后的内容了。

# 知识扩展

## 配置密钥
### 生成密钥对
有些系统对密钥安全等级是有要求的，默认的 `256CRC` 算法可能认证不通过，一般都使用 `rsa` 算法类型：
```
ssh-keygen -t rsa -C "comment"
```
`ssh-keygen` 会默认保存到 `~/.ssh/id_rsa` ，然后它会要求你输入两次密钥口令， `.pub` 文件是你的公钥，另一个则是与之对应的私钥。

如果你不想在使用密钥时输入口令，将其留空即可。 然而，如果你使用了密码，那么请确保添加了 `-o`选项，它会以比默认格式更能抗暴力破解的格式保存私钥，但相应的使用的时候记得输密码，一般留空即可。 

### 部署密钥
现在，进行了上述操作的用户需要将各自的公钥发送给任意一个服务器管理员 （假设服务器正在使用基于公钥的 SSH 验证设置）。 他们所要做的就是复制各自的 `.pub` 文件内容，添加到 Git 的发布key或者系统的 `~/.ssh/authorized_keys` ，一行一个，或者直接通过下方命令完成部署：
```
ssh-copy-id -i ~/.ssh/id_rsa.pub '用户名@服务器地址' -p 'ssh端口'
```
验证密钥是否部署成功，可以用下面的命令测试：
```
ssh -Tv '用户名@服务器地址' -p 'ssh端口'  #测试ssh连接是否成功
```
> 各系统对各种符号的兼容处理可能不同，如配置时百思不得其解可以考虑下比如回车换行兼容问题。

## 修改及配置主题
本包把主题配置文件放到了hexo根目录下，所以只需要修改根目录下配置，如启用 `matery` 主题，则修改 `_config.yml`中：
```yml
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: matery ##表示指向 themes/matery 这个目录
```
然后根据主题说明文档修改 `_config.matery.yml` 这个就可以了，你也可以将该文件删除去修改主题目录下的  `_config.yml` ， `hexo/_config.matery.yml` 这个文件存在就会自动忽略 `hexo/themes/matery/_config.yml` ，新增其他主题方法以此类推。

##  `Git submodule 子模块` 更新
引入 `Git submodule 子模块` 的作用是方便同步上游项目更新，比如主题作者更新内容了想同步，我们只需要运行下方命令更新：
```shell
cd themes/xxx #先切换到对应的主题目录下，目录根据实际情况输
git submodule update
```

> 本包已经把主题配置放到了 `hexo` 配置同级目录，除非配置项发生改变，否则可以大胆更新同步

## 删除 `Git submodule 子模块`
也许有人觉着 `Git submodule 子模块` 挺鸡肋的，那也可以删除掉，没有直接的删除命令，需要手动删除配置信息，以删除一个名为 `assets` 的文件夹为例：

1. 删除子模块文件夹
```
git rm --cached themes/assets
rm -rf assets
```
2. 删除 `.gitmodules` 文件中相关子模块信息
```
[submodule "assets"]
  path = assets
  url = https://github.com/maonx/vimwiki-assets.git
```
3. 删除 `.git/config` 中的相关子模块信息
```
[submodule "assets"]
  url = https://github.com/maonx/vimwiki-assets.git
```
4. 删除 `.git` 文件夹中的相关子模块文件
```
rm -rf .git/modules/assets
```
删除完如果你还需要这个主题，自然是将对应主题文件以普通文件夹的方式整个放到 `themes` 目录，然后当成主仓库的一部分提交，下次每一个改动都体现在主仓库的更改日志中。

# 原文出处
[GoodHexo仓库版使用简介](https://yiwangmeng.com/how-to-use-goodhexo-repo)
