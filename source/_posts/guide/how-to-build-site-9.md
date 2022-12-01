---
title: '从零开始建个小站 - 常见问题'
date: 2022-11-11 11:11:11
categories:
  - 做网站
tags:
  - 教程
---
## 文档看不懂/不想看/太麻烦/我不会……
懒那就没辙了，快发动你的钞能力！

<div style="float:left;border:solid 1px 000;margin:2px;"><img src="https://cdn.jsdelivr.net/gh/828767/static/images/QR-atm.png"  width="200" height="260" ></div>

<div style="float:left;border:solid 1px 000;margin:2px;"><img src="https://cdn.jsdelivr.net/gh/828767/static/images/QR-Taobao.png" width="200" height="260" ></div>

<div style="float:left;border:solid 1px 000;margin:2px;"><img src="https://cdn.jsdelivr.net/gh/828767/static/images/QR-QQ-260489333.png" width="200" height="260" ></div>
<div style="clear:both"></div>


## GitHub咋打不开？
各地网络管制松紧度不一样，无法访问就上梯子吧，配置方法请见：{% post_link guide-how-to-build-site-8 %} 中相关内容。

## 换电脑怎么办
本站提供的仓库方案，只要你仓库不删就不会丢，新电脑上照本站使用教程克隆源码仓库安装一遍本地预览环境就可以了，如果你会遵循Git提交规则，不管到哪有多少个设备都可以一起用，也可以随时恢复到任意一次提交的版本。

## 怎么更换/安装/配置主题？
请打开网站配置文件 `_config.yml` 仔细看下，有更换主题的配置注释。至于主题安装及功能配置，每个主题大同小异，但言而总之，请找到主题的说明文档，根据主题文档去操作。

## 去哪找自己喜欢的主题？
你喜欢啥样的咱也不知道，本站提供的仓库方案中，自带7套精选特色主题，只需要更改网站配置中的主题配置项启用即可。

如果自带的这几套主题都看不上眼，请自行到 [Hexo官方主题展示页](https://hexo.io/themes/) 去挑选，萝卜白菜都是你自己的喜好。

## 关于页面怎么来的？
是自己建的，内容是自己写的，有些主题文档中也会提及，或者请参考：[关于菜单怎么来](https://yiwangmeng.com/common-problems-and-solutions-of-goodhexo#%E5%85%B3%E4%BA%8E%E8%8F%9C%E5%8D%95%E6%80%8E%E4%B9%88%E6%9D%A5)

## 怎么我改了没效果？
任何增删改都需要提交同步到上端仓库，请确保你所做的更改已经提交同步完成，然后等几分钟服务器刷新缓存，对照内容维护可参考：{% post_link guide-how-to-build-site-6 %} 中相关内容。

## 改了几行代码，就异常了
改了啥自己清楚，Git历史记录中也能对比前后差异，所以改完建议本地预览一下结果，启动 `hexo s` 预览的时候就会显示日志，循着异常日志去看下具体什么问题，然后对应修正即可。

或者把错误提示关键词丢给本站战略合作伙伴 Google和百度，让我们的战略伙伴助你一臂之力。

## MarkDown语法我不会😢
MarkDown语法已经很简单易懂了，这里有一个章节列了几个常用到的基本语法： {% post_link guide-how-to-build-site-6 %} ，更多可以阅读后文更专业的MarkDown语法教程。

对照教程敲一两遍就会了，用啥查啥临时抱佛脚都能应付得了。实在不会可以借助编辑器界面化操作，或者你就当Word或记事本写内容都行，无非就是少了点格式样式。