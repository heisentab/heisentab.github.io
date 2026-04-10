---
layout: default
title: 3.3 复数
parent: 3. 基础数据类型
nav_order: 3
---

# 3.3 复数

## 类型

`complex64`（实部虚部各 `float32`）和 `complex128`（各 `float64`）。

## 创建与操作

用 `complex(实部, 虚部)` 构建，`real()` 取实部，`imag()` 取虚部。虚数字面值直接加 `i` 后缀。支持 `==`、`!=` 比较。

```go
x := 1 + 2i
y := 3 + 4i
fmt.Println(x * y)       // (-5+10i)
fmt.Println(real(x * y)) // -5
fmt.Println(imag(x * y)) // 10
fmt.Println(1i * 1i)     // (-1+0i)
```

## math/cmplx 包

提供复数运算函数，如 `Sqrt`、`Abs` 等：

```go
fmt.Println(cmplx.Sqrt(-1)) // (0+1i)
```

---

> 来源：[Go 语言圣经 - 3.3 复数](https://golang-china.github.io/gopl-zh/ch3/ch3-03.html)
