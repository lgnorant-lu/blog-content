---
title: "关于"
date: 2026-07-09
updated: "2026-07-14"
slug: "about"
draft: false
---

> 站点介绍 | 2026-07-14

## 目录
1. [站点](#站点)
2. [怎么访问](#怎么访问)
3. [作者](#作者)

---

## 站点

这是通过 **SSH TUI** 阅读的个人博客。内容在 Git 仓库 `blog-content`，引擎是 Go + Bubbletea + Wish。

- 无 CMS 后台
- Markdown + YAML frontmatter
- FTS5 全文搜索
- 可选 AI / MCP

## 怎么访问

```bash
ssh -p 2222 blog@your-host
# 或（家宽封锁 2222 时）
ssh -p 443 blog@your-host
```

TUI 快捷键：`1` 列表，`2` tags，`3` categories，`4`/`/` 搜索，`5` series，`n`/`p` 邻文，`q` 退出。

## 作者

lgnorant-lu，程序员，喜欢折腾终端与逆向相关主题。
