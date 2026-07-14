---
title: "blog-tui 系列：同步与部署"
date: 2026-07-11
updated: "2026-07-14"
author: "lgnorant-lu"
tags: ["ops", "git", "ssh"]
categories: ["tech"]
keywords: "webhook, deploy key, ssh 443"
series: "blog-tui series"
draft: false
slug: "blog-tui-series-ops"
summary: "Deploy Key + SSH:443、webhook secret、systemd 要点（对应 sync/server 模块）。"
weight: 20
---

## 目录
1. [同步](#同步)
2. [端口](#端口)

---

## 同步

主路径：content remote `ssh://git@ssh.github.com:443/...` + `ssh_key_path`。  
Webhook：`BLOG_TUI_WEBHOOK_SECRET` HMAC。Cron 兜底 pull。

对应代码：`internal/sync`、`internal/server` webhook。

## 端口

| 端口 | 用途 |
|------|------|
| 2222 | TUI SSH |
| 443 | stream 备选 |
| 9000 | webhook |
