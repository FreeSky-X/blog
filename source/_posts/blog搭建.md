---
title: blog搭建
date: 2024-01-09 21:01:43
tags:
---

简单使用 Hexo 构建个人 blog，
推荐 Hexo+Github+Vercel,超级方便最后再加上自己的域名就可以了。

## 初始化 Hexo 项目

[Hexo 官网链接](https://hexo.io/zh-cn/)
确保本地存在 node 开发环境，使用 pnpm 进行包管理。

```bash
# 安装hexo
pnpm install hexo
# 创建你的blog项目
mkdir blog
# 进入blog项目
cd blog
# 初始化hexo blog
npx init
# 启动hexo blog
npx server
```

通过 vscode 打开项目项目结构如下
![](hexofile.png)

## Vercel 平台配置

[Vercel 官网](https://vercel.com)
使用 github 登陆 Vercel 平台。
在 OverView 界面点击 `Add New`-->`Project`,初次使用有可能存在不同
![](vercel_oper1.png)
此处选择 Hexo 项目直接导入，等待 Vercel 平台自动部署
![Alt text](vercel_oper2.png)
部署成功之后可以点击平台生成的链接访问博客(大陆会限制 vercel 的域名，访问链接需要魔法)
![Alt text](vercel_oper3.png)

## 域名配置

此处在[Namesilo](https://www.namesilo.com)上购买域名，该平台支持支付宝支付。同时使用[cloudflare](https://dash.cloudflare.com)托管域名。
这里以域名`free-sky.top`为例，想要通过[https://free-sky.top](https://free-sky.top)访问。

### Vercel 中配置域名

在设置中进行域名配置，填入购买的域名。
![](domains1.png)
![](domains2.png)
选择直接指向而不是重定向
![](domains3.png)

### 进行 cloudflare 配置

Cloudflare 是一个比较常用的国外域名解析服务商，如果你想用 Cloudflare 的 CDN 或者 https 证书，那么必须用他家的域名解析服务。
选择添加站点
![](cf1.png)
输入购买的域名继续，选择免费的套餐就可以了。
![](cf2.png)
添加记录，把默认的记录删除掉。类型选择 A，名称为购买的域名，内容是 vercel 的服务器 IP`76.76.21.21`,代理状态为仅 DNS
![](cf3.png)
![](cf4.png)

开启 https 加密
![](cf5.png)

### NameSilo 配置 Cloudflare 域名解析

确定 dloudflare 的域名解析服务器
![](ns1.png)
登陆 namesilo 进行域名设置,注意这里的用户名是注册时的用户名，不是邮箱
![](ns2.png)
进入个人账户
![](ns3.png)
进入域名管理界面
![](ns4.png)
域名解析服务器修改
![](ns5.png)
把默认的删除掉，添加 Cloudflare 的域名解析服务器，修改之后并提交。
![](ns6.png)

## 完成

访问如[https://free-sky.top](https://free-sky.top),成功
![](success.png)

> 参考链接
> [Vercel 应用绑定自己的域名](https://blog.tangly1024.com/article/vercel-domain)
> [NameSilo 配置 Cloudflare 域名解析教程](https://namesiloyouhui.com/cloudflare-dns-settings.html)
