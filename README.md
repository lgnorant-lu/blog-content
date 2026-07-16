# blog-content

> 博客内容仓库（Markdown 源文件）。  
> 由 blog-tui（SSH TUI 阅读器）和 blog-web（Web 壳）共用。

## 目录结构

```
posts/      已发布的文章（Markdown + Frontmatter）
drafts/     草稿（不发布）
pages/      静态页面（关于、项目等）
templates/  文章模板
config.yaml  站点配置（标题、描述、giscus 仓库等）
```

## 文章 Frontmatter

每篇 `.md` 文件以 YAML frontmatter 开头：

```yaml
---
title: 文章标题
date: 2026-07-01
slug: optional-custom-slug
tags: [tag1, tag2]
series: series-name  # 可选：所属系列
summary: 文章摘要，约 1-2 句
draft: true          # 可选：标记为草稿
---
```

## 发布流程

1. 在 `drafts/` 写作
2. 准备就绪后移至 `posts/`
3. `git push` → Webhook 自动触发重建

## 协议

文章采用 CC BY-NC 4.0，代码片段采用 MIT。
