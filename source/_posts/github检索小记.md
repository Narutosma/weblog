---
title: github检索小记
date: 2024-05-31 00:08:04
categories:
  - git
tags:
  - github
---

# GitHub 检索 🐤

1. in: 根据关键词检索
   关键字：
   name: 项目名称
   description：项目描述
   readme：项目帮助文档
   语法：
   [检索内容] in:name 或 description 或 readme
   单独使用：
2. 检索项目名称包含 Vue 的项目
   Vue in:name
3. 检索项目描述中包含 Vue 的项目
   Vue in:description
4. 检索项目帮助文档中包含 Vue 的项目
   Vue in:readme
   组合使用：
   Vue in:name,description,readme
5. 根据 stars 或 fork 关键词检索
   单独使用：
6. 数量范围：[name] stars:>=[number] | fork:<=[number]
   例：Vue stars:>=2000 或者 Vue fork:<= 2000
7. 区间范围：[name] stars:100..200 fork:200..2000
   例：Vue stars:100..200 或 Vue fork:200..400
   组合使用(关键字用空格分开)
   例：Vue stars:100..200 fork:200..400
8. 显示代码高亮部分
   在 url 链接后面接#[行数]
   例: https://github.com/vuejs/vue/blob/main/src/core/instance/init.ts#L80-L100
9. 检索学习资料 awesome
   语法：awesome 关键字
   例：查找 Vue 学习资料
   awesome Vue
10. 同城 location 和 编程语言 language
    语法：location:地区 language:编程语言
    例：检索长沙玩 java 的
    localtion:changsha language:java
