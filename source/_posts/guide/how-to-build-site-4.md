---
title: '从零开始建个小站 - 2. 拉取仓库到本地'
date: 2022-05-24 20:20:20
categories:
  - 做网站
tags:
  - 教程
---
前面的准备工作已完成，剩下就是将仓库文件克隆同步到本地电脑，方便后续维护与预览。
<!-- more -->
# 2.1 git clone
还是在 `Git Bash` 中，输入这样的命令：
```bash
cd d:\Git   #先切换到要存放Git文件的目录路径
git clone --recurse-submodules 自己的仓库地址 #带子模块一起克隆到本地
```

以上请将仓库地址换成自己的仓库实际地址，建议从仓库页面上复制，获取方法：打开仓库主页》在文件列表右上方有个 `Code` ，点击下拉复制，如下图所示：

![获取项目仓库地址](https://cdn.jsdelivr.net/gh/828767/static/images/github_clone_https_url.png)


# 2.2 安装依赖包
仓库中只包含网站必须的内容源码文件，一些依赖包文件是忽略提交的，所以本地需要重新安装，在仓库根目录路径下运行以下命令：
```bash
npm install
```

以上命令实际上是下载 `package.json` 中定义好的依赖包，等依赖包下载完成，整个本地预览环境就全部安装完成了。


# 2.3 预览测试
在仓库根目录路径下运行 `hexo s` 即可启动预览服务：
```bash
user@IAY MINGW64 /d/Git/action-hexo (main)
$ hexo s
INFO  Validating config
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/ . Press Ctrl+C to stop.
```
以上输出信息中，`/d/Git/action-hexo (main)` 就是所谓 `运行路径` ，Windows系统表示 `d:\Git\action-hexo` 目录，当前在 `main` 分支。

浏览器中打开 `http://localhost:4000` 就可以预览，按 `Ctrl+C` 组合键停止，一些主题或者网站设置变更需要重启该预览服务才能看到效果。

# 2.4 用得到的命令

1. `hexo server` ：开启本地预览服务，默认端口 `4000`，可以添加 ` -p port` 指定预览端口，`Ctrl + C` 关闭，一些网站更改需要重启预览才能看到效果
2. `hexo new "postName"` ：新建文章，`postName` 不建议是中文，也不要添加特殊符号，生成MarkDown 文件在 `source/_post` 目录下，`hexo new` 默认新生成的就是 `post` 类型
3. `hexo new page "pageName"` ：新建页面，会在 `source` 目录下生成 `pageName` 文件夹及对应 `index.md`

上面用到的命令对应缩写：
```bash
hexo s == hexo server
hexo n == hexo new
```

更多命令可自行学习
```bash
hexo help  # 查看帮助
hexo version  #查看Hexo的版本
```
