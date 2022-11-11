---
title: 黑群晖Moments无法显示缩略图，无法转换视频、Video解决
date: 2022-11-10 21:30:00
tags: [折腾]
categories: [黑群晖]
---
# 黑群晖Moments无法显示缩略图，无法转换视频、Video解决

## 问题原因

1. 未洗半白/全白
2. 未替换补丁/未替换ffmpeg

对于第一种情况，根据需要进行洗白，洗白教程看最下方

对于第二种情况，查看**ffmpeg替换**及**Moments补丁替换**

## ffmpeg替换

套件源添加 `https://packages.synocommunity.com/` 并下载ffmpeg

登录root用户，自行搜索 `群晖root权限获取`

```bash
# 备份原始mmfpeg
mv /usr/bin/ffmpeg /usr/bin/ffmpeg_BAK
# 创建第三方ffmpeg软连接
ln -s /volume1/@appstore/ffmpeg/bin/ffmpeg /usr/bin/ffmpeg
```

进入Moments重建索引即可Moments补丁替换教程

由于黑群晖装载大多为6.2.X系统，此系统对转码进行限制，且ffmpeg自带为旧版本，不支持视频等转码

## Moments补丁替换

[补丁下载](https://zyhwjl-my.sharepoint.com/:u:/g/personal/zyhwjl_zyhwjl_cn1/Ed5CxEYGOtZGmh-jVUTnOWEBtMEvzPTQa8twn5zLTOuuxw?e=xwXccT)

1. 停用Moments
2. 使用[WinScp](https://winscp.net/)通过root用户登录
3. 进入目录 `/var/packages/SynologyMoments/target/usr/lib/`
4. 然后将 `libsynophoto-plugin-detection.so` 这个文件，给重命名，备份一下，比如在结尾加上 .bak，进行备份
5. 然后将我们下载的这个补丁，拖入进去
6. 拖入补丁后，我们右键这个补丁，点击属性
7. 设置一下权限，将组和拥有者改成 SynologyMoments，并且将下面权限改成 0755
8. 启用Moments并重建缓存

## 洗白教程

区别：半白无QuickConnect，除此外与全白无任何区别

### 半白

通过Viutul Machine创建虚拟群晖系统获取正版序列号，替换启动盘序列号进行洗白

### 全白

某鱼、某宝购买正版序列号+Mac码并替换启动盘
