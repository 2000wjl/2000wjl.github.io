---
title: Windows将FRP设置为服务并开机自启
date: 2021-03-10 23:44:00
categories: [折腾,实用,内网穿透]
---

# 配置文件

下载[WINSW][1]，将WINSW解压至frp文件夹下，*此一步非必须，只是为了有序。*并重命名为winsw.exe。
在目录下创建winsw.xml文件。*编码必须为UTF-8？*

```html
<service>
    <!-- 该服务的唯一标识 -->
    <id>frp</id>
    <!-- 该服务的名称 -->
    <name>frp0.27.1-windows-amd64</name>
    <!-- 该服务的描述 -->
    <description>frpc客户端 这个服务用 frpc 实现内网穿透</description>
    <!-- 要运行的程序路径 -->
    <executable>D:\Software\frp\frp_0.27.1_windows_amd64\frpc.exe</executable>
    <!-- 携带的参数 -->
    <arguments>-c frpc.ini</arguments>
    <!-- 第一次启动失败 60秒重启 -->
    <onfailure action="restart" delay="60 sec"/>
    <!-- 第二次启动失败 120秒后重启 -->
    <onfailure action="restart" delay="120 sec"/>
    <!-- 日志模式 -->
    <logmode>append</logmode>
    <!-- 指定日志文件目录(相对于executable配置的路径) -->
    <logpath>logs</logpath>
</service>
```

# 使用方法

需管理员权限 

```bash
//注册服务
winsw.exe install
//卸载服务
winsw.exe uninstall
//启动服务
winsw.exe start
//停止服务
winsw.exe stop
//重启服务
winsw.exe restart
//查看状态
winsw.exe status
```

[1]: https://github.com/kohsuke/winsw/releases