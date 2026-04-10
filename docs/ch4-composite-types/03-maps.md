---
layout: default
title: 4.3 Map
parent: 4. 复合数据类型
nav_order: 3
---

# 4.3 Map

## 创建

```go
ages := make(map[string]int)
ages := map[string]int{"alice": 31, "bob": 25}
```

Key 必须支持 `==` 比较。零值为 `nil`，向 `nil` map 写入会 panic。

## 增删改查

```go
ages["alice"] = 32          // 设置
fmt.Println(ages["alice"])  // 读取（不存在返回零值）
delete(ages, "alice")       // 删除
ages["bob"]++               // 递增
```

不能对 map 元素取地址：`&ages["bob"]` 编译报错。

## 判断 key 是否存在

```go
age, ok := ages["bob"]
if !ok { /* bob 不存在 */ }
```

## 遍历

遍历顺序随机，需要有序则先排序 key：

```go
names := make([]string, 0, len(ages))
for name := range ages {
    names = append(names, name)
}
sort.Strings(names)
```

## 用 map 实现 set

```go
seen := make(map[string]bool)
if !seen[line] {
    seen[line] = true
}
```

## 嵌套 map（惰性初始化）

```go
var graph = make(map[string]map[string]bool)
func addEdge(from, to string) {
    if graph[from] == nil {
        graph[from] = make(map[string]bool)
    }
    graph[from][to] = true
}
```

---

> 来源：[Go 语言圣经 - 4.3 Map](https://golang-china.github.io/gopl-zh/ch4/ch4-03.html)
