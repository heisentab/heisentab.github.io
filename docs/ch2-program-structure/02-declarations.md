---
layout: default
title: 2.2 声明
parent: 2. 程序结构
nav_order: 2
---

# 2.2 声明

## 四种声明语句

| 关键字 | 用途 |
|:-------|:-----|
| `var` | 变量声明 |
| `const` | 常量声明 |
| `type` | 类型声明 |
| `func` | 函数声明 |

## 源文件结构

每个 `.go` 源文件的组织顺序：

1. 包声明 — `package xxx`
2. 导入语句 — `import "..."`
3. 包级声明 — 类型、变量、常量、函数（顺序无关）

## 作用域

- 包级声明：整个包的所有源文件中都可访问
- 局部声明（函数内部）：仅在函数内部有效

## 示例

```go
package main
import "fmt"
const boilingF = 212.0  // 包级常量
func main() {
    var f = boilingF          // 局部变量
    var c = (f - 32) * 5 / 9
    fmt.Printf("boiling point = %g°F or %g°C\n", f, c)
}
```

## 函数声明组成

```go
func 函数名(参数列表) 返回值列表 {
    函数体
}
```

- 参数列表：调用者提供的输入值
- 返回值列表：可选，无返回值时省略
- 定义一次，可多处复用

---

> 来源：[Go 语言圣经 - 2.2 声明](https://golang-china.github.io/gopl-zh/ch2/ch2-02.html)
