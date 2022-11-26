---
title: 随身Wifi
date: 2022-11-11 14:44:01
tags: [折腾]
categories: [Linux]
---
随身Wifi是一个装载安卓系统的随身的Wifi发射装置，一般可通过商家内置的eSim进行上网，流量价格一般远低于三大运营商。但商家可通过后台任意设置限速、虚标流量、甚至跑路，所以使用商家的eSim上网并非此装置存在的意义。

而由于商家在此设备后期的流量费用可获得巨大利益，大部分商家将此设备低价甚至亏本销售，以降低用户的试错成本，最终掉入商家的陷阱。

正因此，折腾此设备才有意义。优势：便宜，性能不算太差。

# 分类

主要是根据处理器的不同，主要分为高通410与中兴微两大阵营。两者各有优势，也各有劣势，当然了这里讨论的是未物理升级、加工的设备。

410的优势主要在于有9008，不怕折腾，遇事不决9008，劣势则是信号相对中星微没那么好。发热。

中兴微的优势则在于信号好，不发热，劣势自然就是不能折腾。

## 系统

刷机的话只推荐原版修复或Debian，也就是说不推荐OpenWrt

OpenWrt非常强，对于软路由或者矿渣硬路由来说都是相当不错的选择，然而随身Wifi性能拉跨，加解密能力几乎没有，再加上OpenWrt对信号的影响(限速1Mbps，可能已有解决方案，未深入研究)，且反人类的对时方式 `date -u -s "$(curl 某网址 -kIs | grep Date | awk '{sub(/Jan/,"1"); sub(/Feb/,"2"); sub(/Mar/,"3"); sub(/Apr/,"4"); sub(/May/,"5"); sub(/Jun/,"6"); sub(/Jul/,"7"); sub(/Aug/,"8"); sub(/Sep/,"9"); sub(/Oct/,"10"); sub(/Nov/,"11"); sub(/Dec/,"12"); print $5"-"$4"-"$3,$6;}')"`某些特殊情况仅可此方式对时(来自酷安)，实在不推荐。

目前不清楚OpenWrt的V2在这种特殊情况是否支持域名解析，及USB共享网络是否限速。未验证

### Debian

刷Debian主要是作为服务器使用，如若是特殊情况使用，原版系统就足够，且表现也比Debian好不少

在我使用中将Debian作为Nginx反向代理服务器并将其内网穿透使用，隐藏一些请求的真实IP，还有酷安苏苏小亮亮大佬的[物联网小车项目](https://www.kancloud.cn/a813630449/ufi_car/2795165)其他应用也确实想不到了

### 原版系统

原版系统则可通过酷安水遍大佬的刷机工具折腾，一切都不在话下

## 刷机

### 一般过程

#### 备份

1. 使用水遍大佬提供的miko工具进行救砖包备份
2. 使用高通9008工具对系统各个分区备份
3. 使用星海SVIP对基带备份

#### 刷机

##### 原版系统修改

1. 使用水遍大佬工具修改system分区，主要是开ADB，看切卡密码
2. 刷入修改后的system分区
3. 装面具、Es、6k桌面
4. 修补boot分区
5. 刷入修补的boot分区
6. 刷入插件
7. 折腾->放弃->9008刷救砖包

##### Debian/OpenWrt

1. 重复1、2
2. 执行刷机包的flash.bat(Windows)
3. 重复7

#### Debian相关命令

###### 开机关灯开usb共享网络

```shell
#创建或修改/etc/rc.local并赋予可执行权限
#启动服务systemctl start rc.local

#!/bin/bash
sudo echo none> /sys/class/leds/blue\:wifi_tx/trigger
sudo echo none > /sys/class/leds/green\:wifi_rx/trigger
sudo nmcli c up usb	#usb为名称
```

###### 定时任务

```shell
#修改/etc/crontab文件

1 5 * * * root curl http://192.168.1.1/boaform/admin/formReboot >> /dev/null 2>&1
0 5 * * * root curl "http://192.168.1.1/boaform/admin/formLogin" --data-raw "xxx" >> /dev/null 2>&1
10 8,20 * * * root python3 /root/xx.py >> /root/amar/logTest.txt 2>&1

#重启服务
systemctl restart cron
```

安装python-pip

```shell
apt-get install python-pip -y
```

