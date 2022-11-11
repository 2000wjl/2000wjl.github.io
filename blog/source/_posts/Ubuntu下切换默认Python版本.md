---
title: Ubuntu下切换默认Python版本
date: 2021-05-09 15:33:18
tags: Linux
categories: [Linux,实用]
---

# 以 root 身份登录

首先罗列出所有可用的python 替代版本信息

```bash
update-alternatives --list python
```

这一步可能会报错

```bash
update-alternatives: error: no alternatives for python
```



# 错误信息

如果出现以上所示的错误信息，则表示 Python 的替代版本尚未被update-alternatives 命令识别。想解决这个问题，我们需要更新一下替代列表，将python2.7 和 python3.6 放入其中。

```bash
update-alternatives --install /usr/bin/python python /usr/bin/python2.7 1  
update-alternatives --install /usr/bin/python python /usr/bin/python3.6 2
```

最后的1、2、3...代表序号，后面会有用

# 再次列出可用的 Python 替代版本

```bash
update-alternatives --list python
```



# 切换版本

我们就可以使用下方的命令随时在列出的 Python 替代版本中任意切换了

```bash
update-alternatives --config python
```

输入数字,选择版本



# 查看变化

在terminal中输入

```bash
python
```

