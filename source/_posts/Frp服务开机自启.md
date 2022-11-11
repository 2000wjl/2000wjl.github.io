---
title: Frp服务开机自启
date: 2021-04-12 15:28:07
tags: 折腾
categories: [Linux,实用,内网穿透]
---

# 配置文件

## 创建服务文件

`sudo vim /etc/systemd/system/frps.service`

## 填入如下信息

ExecStart请自行替换

```bash
[Unit]
Description=Frp Server
After=network.target
Wants=network.target

[Service]
Restart=on-failure
RestartSec=5
ExecStart=/usr/local/frp/frps_linux_arm -c /usr/local/frp/frps.ini  #目标文件
#FRPC--ExecStart=/usr/local/frp/frpc_linux_arm -c /usr/local/frp/frpc.ini 

[Install]
WantedBy=multi-user.target
```



使用方法

```bash
#刷新服务列表：
systemctl daemon-reload

#设置开机自启
systemctl enable frps
#关闭开机自启
systemctl disable frps

#启动服务
systemctl start frps
#停止服务
systemctl stop frps
#重启服务
systemctl restart frps
```

