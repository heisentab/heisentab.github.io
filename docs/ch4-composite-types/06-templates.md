---
layout: default
title: 4.6 文本和HTML模板
parent: 4. 复合数据类型
nav_order: 6
---

# 4.6 文本和HTML模板

## 模板语法

模板由普通文本和 `{%raw%}{{action}}{%endraw%}` 组成。`.` 表示当前值，`|` 是管道操作符。

```go
const templ = `{%raw%}{{.TotalCount}}{%endraw%} issues:
{%raw%}{{range .Items}}{%endraw%}----------------------------------------
Number: {%raw%}{{.Number}}{%endraw%}
User:   {%raw%}{{.User.Login}}{%endraw%}
Title:  {%raw%}{{.Title | printf "%.64s"}}{%endraw%}
Age:    {%raw%}{{.CreatedAt | daysAgo}}{%endraw%} days
{%raw%}{{end}}{%endraw%}`
```

## 使用流程

分两步：**解析模板** + **执行模板**。

```go
report, err := template.New("report").
    Funcs(template.FuncMap{"daysAgo": daysAgo}).
    Parse(templ)
```

`template.Must` 解析失败直接 panic，省去手动检查。

## html/template 与自动转义

`html/template` API 与 `text/template` 相同，但会**自动转义** HTML 特殊字符，防止 XSS。若需要输出原始 HTML，用 `template.HTML` 类型标记为受信任内容。

## 要点

- `text/template` 输出纯文本，`html/template` 输出 HTML 并自动转义
- 模板语言支持 `.` 字段访问、`|` 管道、`range` 循环、`if-else`
- `Funcs()` 注册自定义函数后才能在模板中调用

---

> 来源：[Go 语言圣经 - 4.6 文本和HTML模板](https://golang-china.github.io/gopl-zh/ch4/ch4-06.html)
