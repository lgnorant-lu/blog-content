---
title: "blog-tui 系列：引擎与双仓"
date: 2026-07-10
updated: "2026-07-14"
author: "lgnorant-lu"
tags: ["go", "tui", "ssh"]
categories: ["tech"]
keywords: "blog-tui, dual-repo, bubbletea"
series: "blog-tui series"
draft: false
slug: "blog-tui-series-intro"
summary: "说明引擎仓与内容仓职责，以及本地 clone 结构。"
weight: 10
---

## 目录
1. [双仓](#双仓)
2. [模式](#模式)

---

## 双仓

| 仓 | 职责 |
|----|------|
| blog-tui | 引擎：TUI / SSH / HTTP / MCP |
| blog-content | 内容：posts drafts pages config |

本地：`git clone blog-content blog-tui/content`。

## 模式

local、`--serve`、`--http`、`--mcp-serve`。详见引擎仓 docs。
