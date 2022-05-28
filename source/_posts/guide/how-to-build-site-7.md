---
title: '从零开始建个小站 - 实操：打通发布流程'
date: 2022-05-27 20:20:20
categories:
  - 做网站
tags:
  - 教程
---
截止当前，我们已经准备好了建站需要的存储仓库，接着还需要配置相应的权限才能顺利对外发布。

## 配置发布令牌
还记得 GitHub 设置中配置的 `Personal access token` 么，前面叮嘱复制保存下来，下面该派上用场了：

1. 导航到刚创建的项目仓库主页面，在仓库名称下，单击  `Settings（设置）`
   
    ![Settings（设置）](https://docs.github.com/assets/cb-21851/images/help/repository/repo-actions-settings.png)
    
2. 点击左侧的 `Secrets》Actions`，新建仓库机密

    ![新建仓库机密](https://cdn.jsdelivr.net/gh/828767/static/images/repo_set_repo_secret.png)

3. 在 `Name（名称）`输入框中键入机密的名称必须为：`ACTION_ACCESS_TOKEN` ，`Value` 框粘贴之前复制保存的那串值
    
    ![ADD ACTION_ACCESS_TOKEN](https://cdn.jsdelivr.net/gh/828767/static/images/repo_set_repo_secret1.png)

4. 最后单击 `Add secret（添加密码）` 保存完成

    ![ACTION_ACCESS_TOKEN](https://cdn.jsdelivr.net/gh/828767/static/images/repo_set_repo_secret2.png)

## 小试牛刀
经过之前的一番操作，服务器上一切都准备就绪了，可以试试好使与否，直接在项目仓库中触发个提交就行，比如点击 `config.toml` 或 `config.yml` 编辑里面的url，然后保存提交。

![提交变更试效果](https://cdn.jsdelivr.net/gh/828767/static/images/github_commit_first.png)

项目仓库提交变更后，要不了一分钟会自动将源文件渲染并发布到pages仓库，到pages仓库中可见刚从项目仓库提交过来的分支，要对外访问则要设置为pages指定分支。

![自动提交的分支](https://cdn.jsdelivr.net/gh/828767/static/images/github_repo_new_branch.png)

## 设置pages分支
前文已经提到pages分支了，用户pages仓库为：`<owner>.github.io`，其他则为项目仓库，设置方法都是一样的：

1. 导航到pages仓库主页，点击 `Settings（设置）`，点击左侧 `Pages` 标签，选择对应的分支

    ![Pages-branch](https://cdn.jsdelivr.net/gh/828767/static/images/githubpages_select_branch.png)

2. 点击保存后，大约5分钟，就可以通过页面上提示的地址对外访问了。
    
    ![<owner>.github.io](https://docs.github.com/assets/cb-27618/images/help/pages/click-pages-url-to-preview.png)