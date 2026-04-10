---
layout: default
title: 3.2 浮点数
parent: 3. 基础数据类型
nav_order: 2
---

# 3.2 浮点数

## 类型与精度

`float32` 约 6 位十进制精度，最大约 3.4e38；`float64` 约 15 位精度，最大约 1.8e308。优先使用 `float64`，`float32` 误差容易累积：

```go
var f float32 = 16777216 // 1 << 24
fmt.Println(f == f+1)    // true!
```

## 字面值

支持小数（`.707`、`1.`）和科学计数法（`6.02e23`、`6.63e-34`）。

## 格式化

`%g` 紧凑自动、`%f` 定点、`%e` 科学计数法，可指定宽度和精度：

```go
fmt.Printf("x = %d e^x = %8.3f\n", x, math.Exp(float64(x)))
```

## 特殊值

`+Inf`（正无穷）、`-Inf`（负无穷）、`NaN`（非数）。NaN 与任何值比较都为 `false`（包括自身），用 `math.IsNaN()` 检测。

```go
var z float64
fmt.Println(z, -z, 1/z, -1/z, z/z) // 0 -0 +Inf -Inf NaN
nan := math.NaN()
fmt.Println(nan == nan) // false
```

---

> 来源：[Go 语言圣经 - 3.2 浮点数](https://golang-china.github.io/gopl-zh/ch3/ch3-02.html)
