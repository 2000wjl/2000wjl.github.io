---
title: Github项目同步Gitee
date: 2022-11-26 16:21:00
tags: [技术]
categories: [折腾]
---
因某些众所周知的原因，国内时常访问Github不顺畅。以及某些开源协议等相关政策问题，可能某天号和库同时都没了。所以同步到Gitee还是有一定必要的。

> 教程参考[使用Github Actions自动同步到Gitee仓库_让梦想疯狂的博客-CSDN博客](https://blog.csdn.net/qq_21275565/article/details/127689691)

## 操作

### 生成公钥私钥

执行命令：`ssh-keygen -t rsa -C "youremail@example.com"`，连续三次回车，id_rsa 为`私钥`，id_rsa.pub为`公钥`
如果提示：already exists（已经存在），则可以到电脑位置：C:\Users\电脑账号名\ .ssh 直接使用
不使用默认SSH参考：[生成/添加SSH公钥](https://gitee.com/help/articles/4181)

### 在Github项目配置SSH密钥

在Github项目`Settings`->`Secrets`->`Actions`，名称为：`GITEE_RSA_PRIVATE_KEY`，值为：上面生成SSH的`私钥`

### GitHub配置SSH公钥

在Github`Settings`->`SSH and GPG keys`->`New SSH key`，名称为：`GITEE_RSA_PUBLIC_KEY`，值为：上面生成SSH的`公钥`

### Gitee配置SSH公钥

在Gitee`设置`->`安全设置`->`SSH公钥`，标题为：`GITEE_RSA_PUBLIC_KEY`，值为：上面生成SSH的`公钥`

### GitHub创建Github workflow

在Github项目`Actions`创建一个新的workflow

```
name: Sync To Gitee

on: [ push, delete, create ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Sync to Gitee
        uses: wearerequired/git-mirror-action@master
        env:
          # 注意在 Settings->Secrets 配置 GITEE_RSA_PRIVATE_KEY
          SSH_PRIVATE_KEY: ${{ secrets.GITEE_RSA_PRIVATE_KEY }}
        with:
          # 注意替换为你的 GitHub 源仓库地址
          source-repo: git@github.com:github-username/github-repositoryname.git
          # 注意替换为你的 Gitee 目标仓库地址
          destination-repo: git@gitee.com:gitee-username/gitee-repositoryname.git

```

