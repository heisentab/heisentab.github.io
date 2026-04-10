# Go 语言学习博客

基于 [Jekyll](https://jekyllrb.com/) + [just-the-docs](https://just-the-docs.com/) 主题的 Go 语言学习笔记网站，部署在 GitHub Pages 上。

## 快速部署到 GitHub Pages

### 1. 创建 GitHub 仓库

```bash
cd blog
git init
git add .
git commit -m "feat: init go learning blog"
```

在 GitHub 上创建名为 `go-learning` 的仓库（或任意名字），然后推送：

```bash
git remote add origin https://github.com/<你的用户名>/go-learning.git
git branch -M main
git push -u origin main
```

### 2. 启用 GitHub Pages

1. 进入仓库 **Settings → Pages**
2. **Source** 选择 **GitHub Actions**
3. 点击 **Configure** 选择 **Jekyll** workflow，直接 commit

大约 1-2 分钟后，网站就会上线：`https://<你的用户名>.github.io/go-learning/`

### 3. 修改配置

编辑 `_config.yml` 中的 `baseurl` 为你的仓库名：

```yaml
baseurl: "/go-learning"  # 改为你的仓库名
```

## 添加新章节

1. 在 `docs/` 下创建新目录，如 `ch6-methods/`
2. 创建 `index.md` 作为章节入口（设置 `has_children: true`）
3. 创建各小节 `.md` 文件（设置 `parent` 指向父页面标题）
4. 更新 `index.md` 首页的目录表格

### 页面模板

```markdown
---
layout: default
title: 6.1 方法声明
parent: 6. 方法
nav_order: 1
---

# 6.1 方法声明

正文内容...
```

## 本地预览

```bash
# 安装依赖（需要 Ruby）
bundle install

# 启动本地服务器
bundle exec jekyll serve

# 访问 http://localhost:4000/go-learning/
```

## 项目结构

```
blog/
├── _config.yml              # 站点配置
├── Gemfile                   # Ruby 依赖
├── index.md                  # 首页
└── docs/
    ├── ch2-program-structure/ # 第 2 章
    │   ├── index.md
    │   ├── 01-naming.md
    │   ├── 02-declarations.md
    │   └── ...
    ├── ch3-basic-types/       # 第 3 章
    ├── ch4-composite-types/   # 第 4 章
    └── ch5-functions/         # 第 5 章
```
