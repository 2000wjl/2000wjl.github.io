---
title: JavaWeb项目依赖位置的区别
date: 2022-12-16 16:13:00
tags: 学习
categories: [学习,Java]
---
JavaWeb项目常常需要导入一些依赖的jar包，某些时候必须放在WEB-INF/lib下，如mysql驱动。

又有些jar包只需要引入即可，不需要放在WEB-INF/lib中，如tomcat、servlet依赖。

# 原因

仅参与编译检查而不真正参与打包的jar，无需放入WEB-INF/lib下

真正参与打包的jar，必须放在WEB-INF/lib下，否则即使编译通过也无法正常运行，因在运行时缺失依赖
