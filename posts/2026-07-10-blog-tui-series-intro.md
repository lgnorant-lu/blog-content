---
title: "blog-tui 系列：从零搭 SSH 博客"
date: 2026-07-10
updated: "2026-07-14"
author: "lgnorant-lu"
tags: ["go", "tui", "ssh"]
categories: ["tech"]
keywords: "blog-tui, bubbletea, wish ssh, git-based cms"
series: "blog-tui series"
draft: false
slug: "blog-tui-series-intro"
summary: "介绍 blog-tui：用 SSH 与终端 UI 阅读 Git 仓库里的 Markdown 博客。"
weight: 10
---

> 系列首篇 | 2026-07-10 | 原创

## 目录
1. [动机](#动机)
2. [架构一瞥](#架构一瞥)
3. [怎么读](#怎么读)

---

## 动机

传统博客栈偏重 CMS 与浏览器。blog-tui 选择另一条路：内容是普通 Markdown，引擎是 Go TUI，读者通过 SSH 进入。

## 架构一瞥

- 引擎仓 `blog-tui`：扫描、搜索、SSH/HTTP/MCP
- 内容仓 `blog-content`：posts / drafts / pages
- 同步：push → webhook → git pull → 索引重建

## 怎么读

```bash
# 主端口（多数网络）
ssh -p 2222 blog@your-host

# 电信家宽备选（Nginx stream）
ssh -p 443 blog@your-host
```

在 TUI 中：`2` tags，`3` categories，`5` series，`n`/`p` 在过滤列表内切换文章。
