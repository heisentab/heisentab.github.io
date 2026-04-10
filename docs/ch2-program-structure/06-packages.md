---
layout: default
title: 2.6 包和文件
parent: 2. 程序结构
nav_order: 6
---

# 2.6 包和文件

## 包的作用

包是模块化、封装和代码重用的基本单位。一个包由一个或多个 `.go` 文件组成，同一包内的文件共享名字空间。大写开头导出，小写开头不导出。

## 导入包

用 `import` 导入，通过 `包名.成员` 访问。包名默认取导入路径最后一段，可用别名避免冲突。导入了但未使用会编译报错。

```go
import "gopl.io/ch2/tempconv"

fmt.Println(tempconv.CToF(tempconv.BoilingC)) // "212°F"
```

## 包的初始化

包级变量按依赖顺序初始化。复杂初始化用 `init()` 函数，每个文件可定义多个，程序启动时自动按声明顺序调用。

包的初始化自下而上：被依赖的包先初始化，`main` 包最后。每个包只初始化一次。

```go
var a = b + c  // 第三个初始化
var b = f()    // 第二个初始化
var c = 1      // 第一个初始化

func init() { /* 自动调用 */ }
```

---

> 来源：[Go 语言圣经 - 2.6 包和文件](https://golang-china.github.io/gopl-zh/ch2/ch2-06.html)
