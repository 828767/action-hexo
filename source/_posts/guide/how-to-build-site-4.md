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

> 本站方案 `只需要维护私有源码仓库`，所以只需要将 `私有源码仓库` 克隆到本地使用即可，网页会自动发布到对外展示服务仓库对应分支，用户名和对外展示仓库不删不改就行。
>
> 如果改了 GItHub 用户名，请参考 {% post_link guide-how-to-build-site-9 %} 中 `要修改网址怎么办` 中提及项做相应修改。

还是在 `Git Bash` 中，输入这样的命令：
```bash
cd d:\Git   #先切换到要存放Git文件的目录路径
git clone --recurse-submodules 源码仓库地址 #带子模块一起克隆到本地
```

如果第一次克隆时未带 `--recurse-submodules` 参数或者没有完整完成，可以 `在源码仓库根目录路径下` 运行以下命令继续完成子模块更新：
```bash
#请在仓库根目录路径下运行以下命令
git submodule init && git submodule update
```

以上命令中请将 `源码仓库地址` 换成自己的源码仓库实际地址，建议从仓库页面上复制。

仓库地址获取方法：打开源码仓库主页》在文件列表右上方有个 `Code` ，点击下拉复制，如下图所示可选择 `HTTPS`「首选」 或 `SSH`：

![获取项目仓库地址](https://cdn.jsdelivr.net/gh/828767/static/images/github_clone_https_url.png)

{% tabs 仓库链接协议 %}
<!-- tab HTTPS -->

第一次使用 GitHub 账号需要授权，默认会有如下图授权提示弹窗，选择从浏览器登录授权，打开浏览器后按提示输入账号密码登录后点击授权，直到出现授权成功的提示就表示授权成功。

![连接GitHub账号授权](https://cdn.jsdelivr.net/gh/828767/static/images/github-auth-connect.png)

![浏览器登录授权成功](https://cdn.jsdelivr.net/gh/828767/static/images/git-repo-authentication.jpg)

> 如果由于网络原因，`HTTPS` 协议无法拉取/推送仓库，可尝试使用 `SSH` 协议

> **已拉取的仓库修改协议**：用文本编辑器打开仓库目录下的 `.git/config` 修改对应 `url = 复制的仓库地址` ，别修改错了！
>
> 如果涉及到 `submodules`，也请在 `.gitmodules` 中将子模块项目一并修改为 `SSH` 地址

<!-- endtab -->

<!-- tab SSH -->
如果要使用 `SSH` 协议链接，需要先配置 `SSH` 连接密钥。当前 GitHub 强制用户使用超长随机串密码，需要遵循规则使用 `SHA-2` 签名规则密钥。

<div style="padding: 15px; border: 1px solid transparent; border-color: transparent; margin-bottom: 20px; border-radius: 4px; color: #8a6d3b;; background-color: #fcf8e3; border-color: #faebcc;">
<strong>注意：</strong> 
<p>2021年8月14号开始，GitHub弃用账密验证Git操作，改用token或SSH密钥</p>
<p>GitHub 在 2022 年 3 月 15 日通过删除较旧的不安全密钥类型提高了安全性，不再支持 DSA 密钥 (<code>ssh-dss</code>)。</p>
<p>在 2021 年 11 月 2 日之前 <code>valid_after</code> 的 RSA 密钥 (<code>ssh-rsa</code>) 可以继续使用任何签名算法。 在该日期之后生成的 RSA 密钥必须使用 SHA-2 签名算法。 某些较旧的客户端可能需要升级才能使用 SHA-2 签名。</p></div>

## 生成 SSH 密钥对
打开 `Git Bash Here` 或者系统终端，通过以下命令生成私钥和公钥：

```bash
# 生成密钥对，一路回车默认即可
# 如已有其他密钥对在用，自己改下生成的文件名以防覆盖
ssh-keygen -t ed25519 -C "Your_Email"
```

如果您使用的是不支持 `ed25519` 算法的旧系统，请使用：
```bash
ssh-keygen -t rsa -b 4096 -C "Your_Email"
```
更多密钥相关详细信息可参阅 [GitHub官方文档](https://docs.github.com/cn/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

如果你是一路回车生成密钥对，那么生成的密钥对会保存在：`~/.ssh/` 目录下，`~` 表示用户目录，如操作系统登录用户名是 `xyz` ，那么在 Windows 下路径一般为 `C:\Users\xyz\.ssh` ，macOS/Linux下路径为 `/home/xyz/.ssh` ，其中：
```bash
~/.ssh/id_ed25519 //私钥，保存在本地
~/.ssh/id_ed25519.pub //公钥，配置到远端
```

至此，本地 Git 认证环境已准备妥当，下一步将公钥配置到 GitHub 中就能使用了。

## 配置到 GitHub
为了使用方便，直接给 GitHub 添加一个用户密钥，一个密钥可作用于整个账号的增删改查操作。

1. 将 SSH 公钥内容复制到剪贴板「假设都按前面的默认操作」
    <details open><summary>Windows</summary>

    打开 `Git Bash Here` ，复制粘贴如下命令
    ```bash
    clip < ~/.ssh/id_ed25519.pub
    //该命令自动将公钥存到剪贴板，直接用文本编辑器打开公钥再复制也是一样的
    ```

    </details>
    <details><summary>macOS/Linux</summary>

    打开 `Terminal`（终端），复制粘贴如下命令：
    ```bash
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


<!-- endtab -->
{% endtabs %}

# 2.2 安装依赖包
仓库中只包含网站必须的内容源码文件，一些依赖包文件是忽略提交的，所以本地需要重新安装，在仓库 `根目录路径下` 运行以下命令：
```bash
npm install
```

以上命令实际上是下载 `package.json` 中定义好的依赖包，等依赖包下载完成，整个本地预览环境就全部安装完成了。


# 2.3 预览测试
在仓库 `根目录路径下` 运行 `hexo s` 即可启动预览服务：
```bash
user@IAY MINGW64 /d/Git/action-hexo (main)
$ hexo s
INFO  Validating config
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/ . Press Ctrl+C to stop.
```
以上输出信息中，`/d/Git/action-hexo (main)` 就是所谓 `运行路径` ，Windows系统表示 `d:\Git\action-hexo` 目录，当前在 `main` 分支。

浏览器中打开 `http://localhost:4000` 就可以预览，按 `Ctrl+C` 组合键停止预览服务，一些主题或者网站设置变更需要重启该预览服务才能看到效果。

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
