---
layout: default
title: 4.2 Slice
parent: 4. 复合数据类型
nav_order: 2
---

# 4.2 Slice

## 本质

Slice 是对底层数组的引用视图，由三部分组成：**指针**（首元素地址）、**长度**（`len`）、**容量**（`cap`）。多个 slice 可共享同一底层数组。

## 创建

```go
s := []int{1, 2, 3}        // 字面值
s := make([]int, 5)         // len=5, cap=5
s := make([]int, 5, 10)    // len=5, cap=10
```

## 切片操作

`s[i:j]` 返回新 slice，共享底层数组。超过 `cap` 会 panic，超过 `len` 但不超 `cap` 会扩展。

## 与 nil

```go
var s []int    // nil, len=0, cap=0
s = []int{}    // 非 nil, len=0, cap=0
```

判空用 `len(s) == 0`，不要用 `s == nil`。Slice 之间不能用 `==` 比较。

## append

容量足够时原地扩展；不够时分配新数组（通常翻倍），**必须用返回值接收**：

```go
s = append(s, 1)
s = append(s, 2, 3, 4)
s = append(s, other...)
```

## 常用技巧

```go
// 栈
stack = append(stack, v)       // push
top := stack[len(stack)-1]     // peek
stack = stack[:len(stack)-1]   // pop

// 删除元素（保序）
copy(s[i:], s[i+1:])
s = s[:len(s)-1]

// 原地过滤
out := s[:0]
for _, v := range s {
    if keep(v) { out = append(out, v) }
}
```

---

> 来源：[Go 语言圣经 - 4.2 Slice](https://golang-china.github.io/gopl-zh/ch4/ch4-02.html)
