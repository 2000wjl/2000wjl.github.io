---
title: 腾讯云Cloudbase学习记录
date: 2021-03-28 18:22:00
tags: 云开发
categories: [折腾,云开发,腾讯云]
---
# 安装Node.js

安装[Node.js][1]，推荐LTS版本。

# 安装Cloudbase


    npm install -g @cloudbase/cli

国内由于你懂的原因速度较慢，推荐换源后安装。

    npm config set registry https://r.cnpmjs.org/

安装结束后以`cloudbase --version`--`tcb --version`查看是否成功。

# 常用命令

    tcb login                                 #登录
    tcb logout                                #登出
    tcb hosting detail                        #静态网站托管状态
    tcb hosting deploy localpath cloudpath    #静态网站托管部署
    tcb hosting delete cloudpath              #静态网站托管删除
    -e                                        #指定环境id

# 特别的

cloudbaserc.json所在目录下无需-e命令，

> 未识别到有效的环境 Id，请使用 cloudbaserc 配置文件进行操作或通过 -e 参数指定环境 Id


该错误可由此解决。


----------
# 引用
[CloudBase CLI][2]

[1]: https://nodejs.org/en/
[2]: https://www.dazhuanlan.com/2020/03/11/5e6802809511c/