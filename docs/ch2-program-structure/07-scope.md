---
layout: default
title: 2.7 作用域
parent: 2. 程序结构
nav_order: 7
---

# 2.7 作用域

## 作用域 vs 生命周期

**作用域**是名字在源代码中可用的文本区域（编译时概念）；**生命周期**是变量在运行时存在的时间段（运行时概念）。

## 词法域层级

从外到内：全局（`int`、`len`、`true` 等内置名字）→ 包级（同包所有文件可见）→ 文件级（`import` 的包仅当前文件可见）→ 函数/块级（局部变量）。

名字查找从最内层向外查找，内层声明会**屏蔽**外层同名声明。

## 隐式词法域

`for`、`if`、`switch` 的条件/初始化部分会创建隐式词法域：

```go
if f, err := os.Open(fname); err != nil {
    return err
}
f.Close() // 编译错误：f 在 if 外不可见
```

正确做法——需要在外部使用时，提前声明：

```go
f, err := os.Open(fname)
if err != nil {
    return err
}
f.Close() // OK
```

## `:=` 屏蔽陷阱

`:=` 在内部作用域会创建新变量而非更新外部同名变量。修复方法——先声明，用 `=` 赋值：

```go
func init() {
    var err error
    cwd, err = os.Getwd() // 正确更新包级 cwd
}
```

---

> 来源：[Go 语言圣经 - 2.7 作用域](https://golang-china.github.io/gopl-zh/ch2/ch2-07.html)
