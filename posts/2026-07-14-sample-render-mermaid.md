---
title: "样本：render Mermaid 投影"
date: 2026-07-14
updated: "2026-07-14"
author: "lgnorant-lu"
tags: ["render", "mermaid", "test-sample"]
categories: ["tech"]
keywords: "ReplaceMermaidBlocks, mermaid-ascii, TUI-004"
series: "module samples"
draft: false
slug: "sample-render-mermaid"
summary: "特征化样本文：对应 internal/render 与 TUI-004 终端投影。"
weight: 40
---

## 目录
1. [模块](#模块)
2. [图表示例](#图表示例)
3. [相关测试](#相关测试)

---

## 模块

`internal/render.ReplaceMermaidBlocks`：在 Glamour 前将 mermaid 围栏投影为 Unicode 艺术字。

## 图表示例

```mermaid
flowchart LR
  MD[Markdown mermaid] --> R[ReplaceMermaidBlocks]
  R --> G[Glamour ANSI]
```

非法 mermaid 保留源码，不崩溃。

## 相关测试

- `internal/render/mermaid_test.go`
- 冒烟：`test/smoke` 扫描 posts + 投影
