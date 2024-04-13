---
title: wsl2卸载
date: 2024-04-13 20:05:20
tags: [虚拟机,WSL]
---

**Ubuntu 20.04 LTS可以通过Microsoft Store进行安装，但是不能通过Microsoft Store卸载。现列举两种卸载方式。**

### 通过应用与功能卸载

1、查找到安装的ubuntu
![在这里插入图片描述](https://img-blog.csdnimg.cn/caaab42cc7e74f37a8649c7cf3309da9.png#pic_center)

2、卸载
![请添加图片描述](https://img-blog.csdnimg.cn/4183e4c0753d451bbeb4a4f10da32cea.png)

### 通过Windows终端卸载

1、查看当前环境安装的wsl

```
wsl --list
1
```

2、注销（卸载）当前安装的Linux的Windows子系统（名称要与list获取的一致）

```
wsl --unregister Ubuntu-20.04
1
```

3、卸载成功，查看当前安装的Linux的Windows子系统

```
wsl --list
1
```

### 注意

一旦注销，与该发行版相关的所有数据、设置和软件都将永久丢失，三思而后行。

[原文章](https://blog.csdn.net/bmseven/article/details/129365761)
