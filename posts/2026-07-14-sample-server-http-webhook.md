---
title: "样本：server HTTP 与 webhook"
date: 2026-07-14
updated: "2026-07-14"
author: "lgnorant-lu"
tags: ["server", "webhook", "test-sample"]
categories: ["tech"]
keywords: "HTTPServer, WebhookServer, SessionManager, health, feed.xml"
series: "module samples"
draft: false
slug: "sample-server-http-webhook"
summary: "特征化样本文：对应 internal/server 的端点与会话管理测试。"
weight: 30
---

## 目录
1. [模块](#模块)
2. [覆盖场景](#覆盖场景)
3. [日志约定](#日志约定)
4. [相关测试](#相关测试)

---

## 模块

`internal/server`：HTTP（RSS/llms/sitemap/health）、Webhook HMAC、SSH Wish、`SessionManager`。

## 覆盖场景

| 场景 | 期望 |
|------|------|
| /health JSON | status ok + posts |
| /feed.xml | 含标题与链接 |
| /llms.txt /llms-full /sitemap | 200 与字段 |
| webhook 合法签名 push main | ok |
| webhook 坏签名 | 403 |
| SessionManager register/notify | 消息送达 |

## 日志约定

SSH：`ssh session started|ended` 必须带 `session_id`、`remote_addr`（logging.md）。

## 相关测试

- `http_handlers_test.go`、`webhook_http_test.go`、`session_test.go`、`server_test.go`
- 规范目标：server **>50%**
