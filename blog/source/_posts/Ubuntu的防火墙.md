---
title: Ubuntu的防火墙
date: 2021-04-14 15:36:58
tags: Linux
categories: [Linux,实用]
---

# 关闭ubuntu的防火墙 

```bash
ufw disable
```

# 卸载了iptables

```bash
apt-get remove iptables	#重启后即关闭所有防火墙
```

# 开启防火墙

```bash
ufw enable
```

# 关闭ubuntu中的防火墙的其余命令

```bash
iptables -P INPUT ACCEPT``iptables -P FORWARD ACCEPT``iptables -P OUTPUT ACCEPT``iptables -F
```

