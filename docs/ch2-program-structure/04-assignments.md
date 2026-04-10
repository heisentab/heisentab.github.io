---
layout: default
title: 2.4 赋值
parent: 2. 程序结构
nav_order: 4
---

# 2.4 赋值

## 基本赋值

用 `=` 更新变量值，支持复合赋值运算符（`+=`、`*=` 等）。`++` 和 `--` 是语句而非表达式，不能写 `x = i++`。

```go
x = 1
count[x] *= scale
v++
v--
```

## 元组赋值

同时更新多个变量，右边表达式先全部求值再统一赋值，适合交换值等场景。

```go
x, y = y, x           // 交换
i, j, k = 2, 3, 5     // 批量赋值
f, err = os.Open(name) // 多返回值
```

map 查找、类型断言、channel 接收可返回额外的 `ok` 布尔值，用 `_` 丢弃不需要的值。

```go
v, ok = m[key]    // map
v, ok = x.(T)     // 类型断言
v, ok = <-ch      // channel
_, err = io.Copy(dst, src)
```

## 可赋值性

显式赋值、函数传参、返回值、字面量初始化都遵循同一规则：左右类型必须匹配，`nil` 可赋给任何指针或引用类型，常量有更灵活的隐式转换。

---

> 来源：[Go 语言圣经 - 2.4 赋值](https://golang-china.github.io/gopl-zh/ch2/ch2-04.html)
