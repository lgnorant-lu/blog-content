---
title: "blog-tui 系列：部署与内容同步"
date: 2026-07-11
updated: "2026-07-14"
author: "lgnorant-lu"
tags: ["ops", "git", "ssh"]
categories: ["tech"]
keywords: "webhook, git pull, systemd, nginx stream, https token"
series: "blog-tui series"
draft: false
slug: "blog-tui-series-ops"
summary: "生产侧端口、systemd、内容仓 webhook 与 HTTPS token（不写进 remote URL）要点。"
weight: 20
---

> 系列第二篇 | 2026-07-11 | 原创

## 目录
1. [端口](#端口)
2. [同步](#同步)
3. [凭据](#凭据)

---

## 端口

| 端口 | 用途 |
|------|------|
| 22 | 管理 SSH |
| 2222 | blog-tui TUI |
| 443 | Nginx stream → 2222 |
| 9000 | content webhook |

## 同步

`blog-content` push 触发 `:9000/webhook`，服务端 `git pull` 后重建 FTS5。cron 每 5 分钟兜底。

## 凭据

远程 URL 保持干净：

```text
https://github.com/owner/blog-content.git
```

token 放在配置/环境变量（如 `sync.git.https_token: ${BLOG_TUI_GIT_TOKEN}`），由 go-git BasicAuth 注入，并配合 `http_proxy` 访问 GitHub。
