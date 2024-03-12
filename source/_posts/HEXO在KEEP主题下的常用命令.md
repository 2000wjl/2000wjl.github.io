---
title: HEXO在KEEP主题下的常用命令
date: 2024-03-12 15:11:25
tags: [Hexo]
---

# HEXO

全局安装`npm install -g hexo-cli`

局部安装`npm install hexo`

创建文件`hexo new [layout] <title>`

生成`hexo g`

启动`hexo s`

## 版本对应

| Hexo 版本   | 最低版本 (Node.js 版本) | 最高版本 (Node.js 版本) |
| :---------- | :---------------------- | :---------------------- |
| 7.0+        | 14.0.0                  | latest                  |
| 6.2+        | 12.13.0                 | latest                  |
| 6.0+        | 12.13.0                 | 18.5.0                  |
| 5.0+        | 10.13.0                 | 12.0.0                  |
| 4.1 - 4.2   | 8.10                    | 10.0.0                  |
| 4.0         | 8.6                     | 8.10.0                  |
| 3.3 - 3.9   | 6.9                     | 8.0.0                   |
| 3.2 - 3.3   | 0.12                    | 未知                    |
| 3.0 - 3.1   | 0.10 或 iojs            | 未知                    |
| 0.0.1 - 2.8 | 0.10                    | 未知                    |

# KEEP

安装`npm install hexo-theme-keep`

升级`npm install hexo-theme-keep@latest`

# NVM

```shell
##可用版本
nvm list available
##安装指定版本
nvm install 20.9.0
##已安装版本
nvm list
##切换版本
nvm use 14.19.1
```

