---
layout: default
title: 5.1 函数声明
parent: 5. 函数
nav_order: 1
---

# 5.1 函数声明

## 基本语法

```go
func name(parameter-list) (result-list) {
    body
}
```

相同类型的参数可合并书写：

```go
func f(i, j, k int, s, t string)
```

## 返回值

返回值可命名，命名后自动初始化为零值。`_` 表示忽略参数：

```go
func add(x int, y int) int   { return x + y }
func sub(x, y int) (z int)   { z = x - y; return }
func first(x int, _ int) int { return x }
func zero(int, int) int      { return 0 }
```

## 函数签名

函数类型称为**签名**，由参数类型和返回值类型决定，与变量名无关。上面四个函数签名相同：`func(int, int) int`。

## 参数传递

- 无默认参数值，不支持按名传参
- 参数按**值传递**，形参是实参的拷贝
- 引用类型（指针、slice、map、function、channel）可通过间接引用修改原始数据
- 包含返回值的函数必须以 `return` 结尾

---

> 来源：[Go 语言圣经 - 5.1 函数声明](https://golang-china.github.io/gopl-zh/ch5/ch5-01.html)
