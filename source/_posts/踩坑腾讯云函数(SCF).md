---

title: 踩坑腾讯云函数(SCF)
date: 2021-11-30 15:49:21
tags: 踩坑
categories: [踩坑,腾讯云,云函数]
---

> [云函数](https://console.cloud.tencent.com/scf)

# 时区问题

时区默认为UTC+0，如需使用北京时间，须设置环境变量`TZ=Asia/Shanghai`

# 云函数安装依赖

```bash
pip install numpy -t .
//numpy替换为包名，不能省略"."
```