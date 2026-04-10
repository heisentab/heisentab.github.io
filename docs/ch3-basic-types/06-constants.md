---
layout: default
title: 3.6 常量
parent: 3. 基础数据类型
nav_order: 6
---

# 3.6 常量

## 基本特性

`const` 声明，值在编译期确定，不可修改。可批量声明，省略初始化表达式则复用上一行。

```go
const (
    a = 1
    b     // 1
    c = 2
    d     // 2
)
```

## iota 常量生成器

`const` 块中 `iota` 从 0 开始，每行加 1，用于生成枚举或位掩码。

```go
type Weekday int
const (
    Sunday Weekday = iota // 0
    Monday                // 1
    Tuesday               // 2
)

type Flags uint
const (
    FlagUp    Flags = 1 << iota // 1
    FlagBroadcast               // 2
    FlagLoopback                // 4
)
```

存储单位也可用 `iota` 表达：

```go
const (
    _ = 1 << (10 * iota)
    KiB // 1024
    MiB // 1048576
    GiB // 1073741824
)
```

## 无类型常量

未指定类型的常量拥有更高运算精度（至少 256bit），可隐式转换到任意兼容类型。

```go
var x float32 = math.Pi   // 无类型浮点 -> float32
var y float64 = math.Pi   // 无类型浮点 -> float64
```

赋给无显式类型变量时的默认类型：整数 → `int`，浮点 → `float64`，复数 → `complex128`，字符 → `rune`。

注意整数常量除法截断：`5/9` 结果为 0，`5.0/9.0` 结果为 0.555...。

---

> 来源：[Go 语言圣经 - 3.6 常量](https://golang-china.github.io/gopl-zh/ch3/ch3-06.html)
