---
title: '从零开始建个小站 - GitHub设置'
date: 2022-05-24 20:20:20
categories:
  - 做网站
tags:
  - 教程
---
## 注册GitHub账号
如果已有账号则跳过此步骤，直接登录设置即可。如果还没有账号，请访问 https://github.com ，完成注册和邮箱认证，一般用户选择免费套餐就足够用了：

![免费套餐额度](https://cdn.jsdelivr.net/gh/828767/static/images/github.com_join_recommended_plan.png)


## 生成 `Personal access token`
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
