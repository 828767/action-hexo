---
title: '从零开始建个小站 - 配置SSH密钥'
date: 2022-05-25 20:20:20
categories:
  - 做网站
tags:
  - 教程
---
相对于前文提到的 {% post_link guide-how-to-build-site-4 'GitHub设置 - Personal access token' %}，使用 SSH 密钥是另一种更安全的方式。

## 生成SSH密钥
<div style="padding: 15px; border: 1px solid transparent; border-color: transparent; margin-bottom: 20px; border-radius: 4px; color: #8a6d3b;; background-color: #fcf8e3; border-color: #faebcc;">
<strong>注意：</strong> 
<p>2021年8月14号开始，GitHub弃用账密验证Git操作，改用token或SSH密钥</p>
<p>GitHub 在 2022 年 3 月 15 日通过删除较旧的不安全密钥类型提高了安全性，不再支持 DSA 密钥 (<code>ssh-dss</code>)。</p>
<p>在 2021 年 11 月 2 日之前 <code>valid_after</code> 的 RSA 密钥 (<code>ssh-rsa</code>) 可以继续使用任何签名算法。 在该日期之后生成的 RSA 密钥必须使用 SHA-2 签名算法。 某些较旧的客户端可能需要升级才能使用 SHA-2 签名。</p></div>

当前就相当于强制用户使用超长随机串密码，安全加强是好事，遵循规则使用 `SHA-2` 签名规则密钥即可：

```ssh
# 生成密钥对，一路回车默认即可
# 如已有其他密钥对在用，自己改下生成的文件名以防覆盖
ssh-keygen -t ed25519 -C "Your_Email"
```

如果您使用的是不支持 `ed25519` 算法的旧系统，请使用：
```ssh
ssh-keygen -t rsa -b 4096 -C "Your_Email"
```
更多密钥相关详细信息可参阅 [GitHub官方文档][new-SSH-key]

如果你是一路回车生成密钥对，那么生成的密钥对会保存在：`~/.ssh/` 目录下，`~` 表示用户目录，如操作系统登录用户名是 `xyz` ，那么在Windows下路径则为 `C:\Users\xyz\.ssh` ,macOS/Linux下路径为 `/home/xyz/.ssh` ，其中：
```ssh
~/.ssh/id_ed25519 //私钥，保存在本地
~/.ssh/id_ed25519.pub //公钥，配置到异端
```

到此，本地Git环境已准备妥当，下一步将公钥配置到GitHub中就能使用了。


## 配置密钥

为了使用方便，给GitHub添加一个用户密钥，一个密钥可作用于整个账号的增删改查操作。

1. 将 SSH 公钥内容复制到剪贴板「假设都按前面的默认操作」
    <details open><summary>Windows</summary>

    打开 `Git Bash` ，复制粘贴如下命令
    ```ssh
    clip < ~/.ssh/id_ed25519.pub
    //该命令自动将公钥存到剪贴板，直接用文本编辑器打开公钥再复制也是一样的
    ```

    </details>
    <details><summary>macOS/Linux</summary>

    打开 Terminal（终端），复制粘贴如下命令：
    ```ssh
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