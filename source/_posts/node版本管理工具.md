---
title: Node版本管理工具 MacOS
date: 2024-05-31 00:02:26
categories:
  - node
tags:
  - 工具
---

# Node 版本管理工具 MacOS

- 全局安装 n 模块：sudo npm install n -g
- 安装当前稳定版本：sudo n stable
- 安装最新版本：sudo n latest
- node 版本降级/升级（安装指定版本）：sudo n 版本号 例：sudo n 14.20.1
- 卸载指定 node 版本：sudo n rm 版本号
- 检测目前安装了哪些版本：n
- 切换 node 版本（不会删除已安装的其他版本）：sudo n 版本号
- 更新 npm 到最新版本：sudo npm install npm@latest -g
- 查看版本号：node -v
