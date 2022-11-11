---
title: linux下开启SSH
date: 2021-04-14 15:39:14
tags: Linux
categories: [Linux,实用]
---

```bash
#若无vim ，则安装。或安装宝塔自动安装
sudo apt-get update
sudo apt-get install vim
#查找并修改以下数据
sudo vi /etc/ssh/sshd_config
-->
PermitRootLogin yes #允许root登录
PasswordAuthentication yes # 设置是否使用口令验证。
#设置root密码
sudo -i
passwd #输入密码无提示
#修改后重启ssh服务
service sshd restart # 或者
/etc/initd .d /sshd restart
```

