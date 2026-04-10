# Go 语言学习博客

基于 Jekyll + just-the-docs 主题的 Go 语言学习笔记，部署在 GitHub Pages。

## 部署

将此仓库推送到名为 `<username>.github.io` 的 GitHub 仓库，GitHub Pages 会自动构建。

访问地址：`https://<username>.github.io/`

## 添加新章节

1. 在 `docs/` 下创建目录，如 `ch6-methods/`
2. 创建 `index.md`（设置 `has_children: true`）
3. 创建各小节 `.md` 文件（设置 `parent` 指向父页面标题）

页面模板：

```markdown
---
layout: default
title: 6.1 方法声明
parent: 6. 方法
nav_order: 1
---
```

## 本地预览

```bash
bundle install
bundle exec jekyll serve
```
