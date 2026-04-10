---
layout: default
title: 5.2 递归
parent: 5. 函数
nav_order: 2
---

# 5.2 递归

函数可以直接或间接调用自身。递归适合处理树形等递归数据结构。

## 示例：提取 HTML 链接

```go
func visit(links []string, n *html.Node) []string {
    if n.Type == html.ElementNode && n.Data == "a" {
        for _, a := range n.Attr {
            if a.Key == "href" {
                links = append(links, a.Val)
            }
        }
    }
    for c := n.FirstChild; c != nil; c = c.NextSibling {
        links = visit(links, c)
    }
    return links
}
```

## 示例：输出文档结构

```go
func outline(stack []string, n *html.Node) {
    if n.Type == html.ElementNode {
        stack = append(stack, n.Data)
        fmt.Println(stack)
    }
    for c := n.FirstChild; c != nil; c = c.NextSibling {
        outline(stack, c)
    }
}
```

只有入栈没有出栈——因为 `append` 操作的是 slice 拷贝，返回后调用方的 `stack` 不受影响。

## Go 的可变栈

多数语言固定大小调用栈（64KB~2MB），深递归可能栈溢出。Go 使用**可变栈**，初始很小，按需自动增长，无需担心栈溢出。

---

> 来源：[Go 语言圣经 - 5.2 递归](https://golang-china.github.io/gopl-zh/ch5/ch5-02.html)
