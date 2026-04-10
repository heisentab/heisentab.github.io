---
layout: default
title: 5.5 函数值
parent: 5. 函数
nav_order: 5
---

# 5.5 函数值

Go 中函数是**第一类值**：可以赋值给变量、作为参数传递、作为返回值。

## 基本用法

```go
f := square        // f 类型是 func(int) int
fmt.Println(f(3))  // 9
f = negative
fmt.Println(f(3))  // -3
```

- 函数类型零值是 `nil`，调用 `nil` 函数会 panic
- 函数值可以与 `nil` 比较，但函数值之间**不可比较**

## 用函数值参数化行为

```go
func add1(r rune) rune { return r + 1 }
fmt.Println(strings.Map(add1, "HAL-9000")) // "IBM.:111"
```

## 示例：通用节点遍历

将遍历逻辑与操作逻辑分离：

```go
func forEachNode(n *html.Node, pre, post func(n *html.Node)) {
    if pre != nil {
        pre(n)
    }
    for c := n.FirstChild; c != nil; c = c.NextSibling {
        forEachNode(c, pre, post)
    }
    if post != nil {
        post(n)
    }
}
```

核心价值：不仅能通过**数据**参数化函数，还能通过**行为**参数化函数。

---

> 来源：[Go 语言圣经 - 5.5 函数值](https://golang-china.github.io/gopl-zh/ch5/ch5-05.html)
