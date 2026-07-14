---
title: "样本：sync 拉取与监听"
date: 2026-07-14
updated: "2026-07-14"
author: "lgnorant-lu"
tags: ["sync", "git", "test-sample"]
categories: ["tech"]
keywords: "GitPuller, Watcher, isRelevant, https_token, ssh_key_path"
series: "module samples"
draft: false
slug: "sample-sync-gitpull"
summary: "特征化样本文：对应 internal/sync 的 pull 鉴权与 fsnotify 行为。"
weight: 20
---

## 目录
1. [模块](#模块)
2. [覆盖场景](#覆盖场景)
3. [相关测试](#相关测试)

---

## 模块

`internal/sync`：`GitPuller`（SSH key / HTTPS token / proxy）、`Watcher`（debounce、仅 `.md`）。

## 覆盖场景

| 场景 | 期望 |
|------|------|
| NewGitPullerWithConfig | 字段注入 |
| buildAuth 缺 key / token | error 或 BasicAuth |
| isRelevant md write/create | true |
| isRelevant txt / chmod | false |
| Watcher 创建 .md | 通知；.txt 不通知 |

## 相关测试

- `gitpull_test.go`、`watcher_test.go`、`isrelevant_test.go`
- 规范目标：sync **>80%**
