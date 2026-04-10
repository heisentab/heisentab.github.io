---
layout: default
title: 2.3 变量
parent: 2. 程序结构
nav_order: 3
---

# 2.3 变量

## 变量声明

`var 变量名 类型 = 表达式`，类型和表达式可省其一。省类型则自动推导，省表达式则用零值：数值 `0`、布尔 `false`、字符串 `""`、引用类型和接口 `nil`。Go 不存在未初始化的变量。

```go
var i, j, k int
var b, f, s = true, 2.3, "four"
var f, err = os.Open(name)
```

## 简短变量声明

函数内用 `:=` 声明局部变量，自动推导类型。`:=` 是声明，`=` 是赋值。多变量时至少一个是新变量，否则编译报错。

```go
freq := rand.Float64() * 3.0
in, err := os.Open(infile)
out, err := os.Create(outfile) // err 已存在，仅赋值
```

## 指针

`&x` 取地址，`*p` 读写指向的值，零值为 `nil`。返回局部变量地址是安全的，变量会自动逃逸到堆上。

```go
x := 1
p := &x  // *int
*p = 2   // x == 2
```

## new 函数

`new(T)` 返回零值初始化的 `*T`，等价于声明变量后取地址，是语法糖。`new` 是预定义函数，非关键字，可被重定义。

```go
p := new(int) // *p == 0
```

## 生命周期

包级变量与程序同生命周期。局部变量不再被引用时可回收。编译器通过**逃逸分析**决定栈/堆分配——地址被外部引用则逃逸到堆，否则可留在栈上，与用 `var` 还是 `new` 无关。

---

> 来源：[Go 语言圣经 - 2.3 变量](https://golang-china.github.io/gopl-zh/ch2/ch2-03.html)
