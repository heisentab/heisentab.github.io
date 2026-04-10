---
layout: default
title: 3.4 布尔型
parent: 3. 基础数据类型
nav_order: 4
---

# 3.4 布尔型

值为 `true` 或 `false`。`&&`（AND）和 `||`（OR）有短路行为，`&&` 优先级高于 `||`。`!` 为逻辑非。

```go
s != "" && s[0] == 'x' // 安全：s 为空时不会执行 s[0]
```

布尔与数字不能隐式转换，需手动处理：

```go
func btoi(b bool) int { if b { return 1 }; return 0 }
func itob(i int) bool { return i != 0 }
```

---

> 来源：[Go 语言圣经 - 3.4 布尔型](https://golang-china.github.io/gopl-zh/ch3/ch3-04.html)
