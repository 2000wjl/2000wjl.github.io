---
title: 远程桌面添加SSL
date: 2020-12-18 12:41:00
tags:
categories: [折腾,实用]
---

ssl是数字证书的一种，简而言之是为了验证客户端与服务器的连接是否安全。启用ssl后，所有数据将通过加密协议传输，避免明文传输密码而带来的风险。

## 申请ssl证书
本部分不多赘述，网上有大量教程。不过值得一提的是，不同的客户端对不同的颁发机构信任不一。另外如果需要泛域名证书一般需要进行企业认证、付费等，或通过[Let's Encrypt](https://letsencrypt.org/)免费申请，但由于相关原因部分客户端不信任该颁发机构，请自行斟酌。
## 添加ssl证书
本教程理论适用于windows所有操作系统，本人使用win10 20H2测试可用。--2020.12.18
使用mmc（命令行运行）,然后文件->添加/删除管理单元->证书->**计算机账户**->本地计算机(运行此XXXXX)，然后在左侧控制台节点的证书->个人下，右键单击右侧空白->所有任务->导入，然后按提示选择刚才的.p12`另见补充说明`文件，并输入正确的密码。

## 为RDS指定证书
注册表`regedit(CMD)`路径为 `计算机\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp`
加入如下项
`Value name: SSLCertificateSHA1Hash`
`Value type: REG_BINARY（二进制值）`
`Value data:<certificate thumbprint>（证书指纹）`
其中Value data为可以在刚才加入的证书窗口查到的颁发下来的SSL证书的sha1指纹（20个16进制数），这里貌似不能直接复制粘贴，手动敲一遍也还好，反正不多，注意别抄错就好。
## 为证书配置权限
在刚才的mmc控制台，选中你的证书右键->所有任务->管理私钥，弹出的窗口和NTFS的权限管理窗口类似，在权限对话框中选添加，用户名直接输入 NETWORK SERVICE 并检查，通过后确定添加，然后保证权限中的读取为挑勾选中状态即可。
## 结语
如果证书过期或其它原因导致需要替换新的证书时，需要在重新导入证书，设置私钥访问权限设置新的fingerprint后，重启系统才能生效。


----------
## **参考文章**
[使用StartSSL(Let’s Encrypt)的免费SSL证书为Windows远程桌面RDS服务指定受信任的证书](https://blog.k-res.net/archives/1893.html)
[SSL certificates with StartSSL, Microsoft IIS, Microsoft RDP and OpenSSL ](http://teenteam.biz/teenteam/blog/?p=11/)
[How to Force Remote Desktop Services on Windows 7 to Use a Custom Server Authentication Certificate for TLS](https://support.microsoft.com/en-us/kb/2001849)

## **补充**
某些证书颁发者未使用默认的.p12文件，但一般会颁发证书加私钥的形式，若没有私钥，如crt格式，则无法配置权限。如某讯云格式则需导入pfx后输入txt中的私钥。

另外，经此方法配置加密传输后，在较低版本的RD客户端不信任远程电脑。实测Window 7及以上无此问题。