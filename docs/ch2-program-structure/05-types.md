---
layout: default
title: 2.5 类型
parent: 2. 程序结构
nav_order: 5
---

# 2.5 类型

## 类型声明

`type 类型名 底层类型` 创建新类型，与底层类型结构相同但不兼容，防止不同概念混用。首字母大写可导出。

```go
type Celsius float64
type Fahrenheit float64
```

`Celsius` 和 `Fahrenheit` 底层都是 `float64`，但不能直接比较或混合运算，需显式转换。

## 类型转换

`T(x)` 将 `x` 转为类型 `T`，底层类型相同时只改类型不改值。数值类型间转换可能丢精度。

```go
fmt.Println(c == Celsius(f))  // OK，显式转换后比较
```

## 方法

命名类型可定义方法。定义 `String()` 方法后，`fmt` 打印时自动调用。

```go
func (c Celsius) String() string { return fmt.Sprintf("%g°C", c) }
c := FToC(212.0)
fmt.Println(c) // "100°C"
```

---

> 来源：[Go 语言圣经 - 2.5 类型](https://golang-china.github.io/gopl-zh/ch2/ch2-05.html)
