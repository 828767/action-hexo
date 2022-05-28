---
title: '从零开始建个小站 - 实操：个性设置'
date: 2022-05-30 20:20:20
categories:
  - 做网站
tags:
  - 教程
---
项目仓库克隆下来，网站的各项设置都是默认的，一些标题，作者之类的需要根据自己的实际情况进行修改，个性设置主要是网站根目录的框架配置和主题配置。好在 `hugo` 和 `hexo` 配置结构大同小异，而且都支持将配置文件放在网站根目录下，只需要修改配置，今后主题更新只需要同步配置其他也互不影响。

> **每套用一个主题，渲染出来的网站界面和功能都有所不同，所以除了基础配置，各个主题设计的配置项都可能不一样，所以一定要依照主题模板文档去配置！！！**

> **一定要依照主题模板文档去配置！！！**

> **一定要依照主题模板文档去配置！！！**

## Hugo

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


## Hexo

和Hugo一样，Hexo内容个性化也是靠配置文件完成，展示个性化根据主题而定。Hexo主题可以到 [官网主题页][Hexo主题] 去挑选：

![Hexo官网主题页](https://cdn.jsdelivr.net/gh/828767/static/images/hexo-themes.png)

配置文件包含根目录下的 `_config.yml` 和主题目录下的 `_config.yml` ，在新版中这俩配置可以合而为一，也可以将主题目录下的 `_config.yml` 移到根目录下命名为： `_config.主题名称.yml` ，如  `_config.maupassant.yml` 表示主题 `maupassant` 的配置，详见 [Hexo主题配置说明][Hexo主题配置]。

配置优先级为：项目网站根目录下的 `_config.yml` 》 `_config.maupassant.yml` 》主题目录下的 `_config.yml` ，**建议使用 `_config.主题名称.yml` 方式存储主题配置**。

Hexo和Hugo一样，基础配置较少，剩下的**请参照主题文档配置！请参照主题文档配置！请参照主题文档配置！**


[hogo-install]: https://gohugo.io/getting-started/installing/ "Hugo官方安装文档"
[hugo-config]: https://gohugo.io/getting-started/configuration/ "Hugo官方配置说明"
[Hugo主题]: https://themes.gohugo.io/ "Hugo官方主题展示页"
[Hexo主题]: https://hexo.io/themes/ "Hexo官方主题展示页"
[Hexo主题配置]: https://hexo.io/zh-cn/docs/configuration#%E4%BD%BF%E7%94%A8%E4%BB%A3%E6%9B%BF%E4%B8%BB%E9%A2%98%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6 "使用代替主题配置文件"
