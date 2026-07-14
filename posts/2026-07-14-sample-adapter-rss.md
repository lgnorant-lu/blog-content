---
title: "样本：adapter RSS 解析"
date: 2026-07-14
updated: "2026-07-14"
author: "lgnorant-lu"
tags: ["adapter", "rss", "test-sample"]
categories: ["tech"]
keywords: "RSSAdapter, parseRSS, stripHTML, QueryPosts"
series: "module samples"
draft: false
slug: "sample-adapter-rss"
summary: "特征化样本文：对应 internal/adapter 覆盖目标与测试场景。"
weight: 10
---

## 目录
1. [模块](#模块)
2. [覆盖场景](#覆盖场景)
3. [相关测试](#相关测试)

---

## 模块

`internal/adapter`：`RSSAdapter`、`parseRSS`（RSS2/Atom）、`stripHTML`、`FetchGiscusComments`。

## 覆盖场景

| 场景 | 期望 |
|------|------|
| RSS 2.0 双条目 | 解析 title/slug/date |
| Atom 单条目 | 解析 link href |
| 非法 feed | error |
| httptest QueryPosts + Limit | Source 填充、截断 |
| Giscus 空参 / 200 / 4xx / 坏 JSON | 分支全覆盖 |

## 相关测试

- `rss_test.go`、`rss_parse_test.go`、`giscus_test.go`
- 规范目标：adapter **>80%**
