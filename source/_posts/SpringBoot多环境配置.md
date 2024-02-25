---
title: Spring Boot 多环境配置
date: 2024-02-26 00:50:49
tags:
  - Java
  - 环境配置
categories: 
  - 后端
---
# Spring Boot 多环境配置

## 什么是多环境配置?

在日常的开发工作中，我们的应用程序往往需要在不同的环境中运行，例如：开发环境、测试环境和生产环境。每个环境中的配置参数可能都会有所不同，例如数据库连接信息、文件服务器的 IP 地址等。Spring Boot 提供了非常方便的方式来管理这些不同环境的配置。

## Spring Profile 介绍

Spring Profile 是 Spring 框架用于处理不同环境配置的解决方案。Profile 可以帮助我们在不改变应用代码的情况下，根据当前环境动态地激活或者切换不同的配置。

当你激活一个特定的 Profile 时，Spring Boot 会查找名为 `application-{profile}.yml` 的文件，并把其中的属性加载到 Spring Environment 中。

## 创建和使用Profile

假设我们有三个环境：开发（`dev`）、测试（`test`）、生产（`prod`）。那么我们可以创建以下几个配置文件：

- `application.yml`: 存放所有环境通用的配置。
- `application-dev.yml`: 存放开发环境的特殊配置。
- `application-test.yml`: 存放测试环境的特殊配置。
- `application-prod.yml`: 存放生产环境的特殊配置。

## 激活Profile

 **在 `application.yml` 中设置 `spring.profiles.active` 属性**。

```yml
# 激活 dev 环境
spring:
	profiles:
		active: dev
```

