---
title: '从零开始建个小站 - 实操：准备存储仓库'
date: 2022-05-26 20:20:20
categories:
  - 做网站
tags:
  - 教程
---

本实操仅针对 {% post_link guide-how-to-build-site-2 "建站方案选择" %} 中提及的免费方案：**hugo/hexo + GitHub + GitHub免费二级域名/自备域名**，另外的付费方案自带网站后台，界面化的一体操作没什么好演示的，如有需要可求助我们的战略合作伙伴Google和百度。

## 建立存储仓库
虽然可以通过分支控制源文件和对外访问文件，但还是建议分仓库存储：
1. **公开：GitHubPages仓库**：页面文件对外访问
2. **私有：项目仓库**：存储网站源文件，只有自己可见防止提交记录、网站配置等机密信息外泄

### **公开：GitHubPages仓库**
1. 登录GitHub，在任何页面的右上角，使用 `+` 下拉菜单选择 `New repository（新建仓库）`
    
    ![新建GitHubPages仓库](https://docs.github.com/assets/cb-11427/images/help/repository/repo-create.png)

2. 因为要对外访问，所以名称必须为：`<owner>.github.io`，且可见性必须为 `public(公开)`：
    
    ![username.github.io](https://docs.github.com/assets/cb-34195/images/help/pages/create-repository-name-pages.png)
    ![可见性选public(公开)](https://docs.github.com/assets/cb-20877/images/help/repository/create-repository-public-private.png)

3. 此时只是个空仓库备用，等有提交了再来设置pages
   
### **私有：项目仓库**
项目仓库保存着网站的源代码，控制网站的输出内容和页面样式。这里用导入模板仓库的方法，快速生成具有与模板仓库相同的目录结构和文件的新仓库，该模板仓库实现功能：
- 自动将源文件渲染并发布到GitHubPages仓库pages分支
- 自动判断配置的网站域名，并决定是否需要绑定 `CNAME`
- 自动渲染发布到当前项目仓库pages分支，如果不设置为私有仓库可作为项目主页访问
- pages分支只保留最后1次提交记录

1. 打开 [这个模板仓库](https://github.com/828767/ "hugo/hexo框架模板") 主页面，根据自己的需求选择 `action-hugo` 或者 `action-hexo` 等仓库任选其一
2. 在文件列表上方，单击 `Use this template（使用此模板）`
    
    ![使用模板](https://docs.github.com/assets/cb-36544/images/help/repository/use-this-template-button.png)

3. 输入你想要的仓库名称和描述（可选），网站源码仓库可见性建议选择 `Private（私有）`

    ![项目仓库名称](https://docs.github.com/assets/cb-25139/images/help/repository/create-repository-name.png)

4. （可选）要包括模板中所有分支的目录结构和文件，而不仅仅是默认分支，请勾选 `Include all branches（包括所有分支）`
5. 最后点击 `Create repository from template（从模板创建仓库）`