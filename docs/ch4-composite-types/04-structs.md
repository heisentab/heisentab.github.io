---
layout: default
title: 4.4 结构体
parent: 4. 复合数据类型
nav_order: 4
---

# 4.4 结构体

## 定义与访问

结构体将多个不同类型的值聚合为一个实体。用 `.` 访问成员，指针也可直接用 `.`（自动解引用）。

```go
type Employee struct {
    ID     int
    Name   string
    Salary int
}
var e Employee
ptr := &e
ptr.Name = "Bob"  // 等价于 (*ptr).Name = "Bob"
```

## 字面值

按顺序赋值（必须全部指定）或按名字赋值（可省略，省略的为零值），不能混用。

```go
p := Point{1, 2}      // 按顺序
p := Point{Y: 2}      // 按名字，X 为 0
pp := &Point{1, 2}    // 直接取地址
```

## 比较

所有成员可比较时，结构体支持 `==` 和 `!=`，可用作 map 的 key。

## 匿名嵌入

只写类型不写名字，可通过简短路径直接访问嵌套成员，同时继承嵌入类型的方法。

```go
type Circle struct {
    Point           // 匿名嵌入
    Radius int
}
var c Circle
c.X = 8  // 等价于 c.Point.X = 8
```

字面值初始化时仍需写完整层级。匿名嵌入是 Go **组合复用**的核心机制（替代继承）。

## 递归结构

结构体不能包含自身，但可包含自身的指针：

```go
type tree struct {
    value       int
    left, right *tree
}
```

---

> 来源：[Go 语言圣经 - 4.4 结构体](https://golang-china.github.io/gopl-zh/ch4/ch4-04.html)
