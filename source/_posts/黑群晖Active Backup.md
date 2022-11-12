---
title: 黑群晖Active Backup
date: 2022-11-12 14:51:00
tags: [黑群晖]
categories: [黑群晖]
---
Active Backup是一款群晖官方套件，主要用于备份实体机、虚拟机等，支持全量、增量备份

黑群晖使用此套件需要激活，白群晖直接登录即可使用

#### 环境

`群晖6.2.3 型号 918+`

#### 激活

```
https://地址:端口/webapi/auth.cgi?api=SYNO.API.Auth&method=Login&version=1&account=管理员账户&passwd=管理员密码

https://地址:端口/webapi/entry.cgi?api=SYNO.ActiveBackup.Activation&method=set&version=1&activated=true&serial_number=%22你的序列号%22
```

#### 使用
