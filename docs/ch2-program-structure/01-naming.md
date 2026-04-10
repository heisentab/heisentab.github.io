---
layout: default
title: 2.1 命名
parent: 2. 程序结构
nav_order: 1
---

# 2.1 命名

## 基本规则

- 名字必须以**字母（Unicode）或下划线**开头，后跟任意数量的字母、数字或下划线
- 大小写敏感：`heapSort` 和 `Heapsort` 是不同的名字

## 关键字（25 个，不可用作自定义名）

```
break      default       func     interface   select
case       defer         go       map         struct
chan       else          goto     package     switch
const      fallthrough   if       range       type
continue   for           import   return      var
```

## 预定义名字（可重定义，但需谨慎）

| 类别 | 名字 |
|:----:|------|
| 常量 | `true` `false` `iota` `nil` |
| 类型 | `int` `int8` `int16` `int32` `int64` `uint` `uint8` `uint16` `uint32` `uint64` `uintptr` `float32` `float64` `complex128` `complex64` `bool` `byte` `rune` `string` `error` |
| 函数 | `make` `len` `cap` `new` `append` `copy` `close` `delete` `complex` `real` `imag` `panic` `recover` |

## 作用域与可见性

- 函数内部定义 → 仅函数内有效
- 函数外部定义 → 当前包所有文件可访问
- **大写字母开头** → 导出（包外可访问），如 `fmt.Printf`
- **小写字母开头** → 未导出（仅包内可见）
- 包名一般用小写字母

## 命名风格

- 推荐**驼峰式（camelCase）**，不用下划线分隔
- 局部变量倾向短名字（如 `i`），作用域大的用长名字
- 缩略词保持全大写或全小写：`HTMLEscape`、`escapeHTML`（不用 `escapeHtml`）

---

> 来源：[Go 语言圣经 - 2.1 命名](https://golang-china.github.io/gopl-zh/ch2/ch2-01.html)
