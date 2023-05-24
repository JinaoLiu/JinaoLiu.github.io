---
layout:     post
title:      GitHub Actions使用
subtitle:   技术博客
date:       2023-05-24
author:     jinaoliu
header-img: img/post-bg-cook.jpg
catalog: true
tags:		
    - 总结	
---



# &#x1F3AF;&#x1F3AF;&#x1F3AF; GitHub Actions使用

## &#x1F449; GitHub Actions介绍

具体关于这一块的介绍, 就不细说了, 这里列出两个资源, 特别是GitHub自己的官方文档关于GitHub Actions的使用写的非常详细.

- https://docs.github.com/zh/actions/learn-github-actions
- https://www.bilibili.com/video/BV1RE411R7Uy

## &#x1F680;&#x1F680;&#x1F680;我的练习

我设计的功能是: 7天内不活跃的issue将会被关闭, 以下是代码实现.

```yaml
name: Issue Close

on:
  schedule:
    - cron: "0 0 * * *"

jobs:
  close-issues:
    runs-on: ubuntu-latest
    steps:
      - name: close-issues
        uses: actions-cool/issues-helper@v1.7
        with:
          actions: 'close-issues'
          token: ${{ secrets.GITHUB_TOKEN }}
          inactive-day: 7
```



