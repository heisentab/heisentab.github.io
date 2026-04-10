---
layout: default
title: 4.5 JSON
parent: 4. 复合数据类型
nav_order: 5
---

# 4.5 JSON

## 编码（Marshal）

`json.Marshal` 将 Go 值转为 JSON，只编码导出的成员。`json.MarshalIndent` 生成可读格式。

```go
data, err := json.Marshal(movies)
data, err := json.MarshalIndent(movies, "", "    ")
```

## 解码（Unmarshal）

`json.Unmarshal` 将 JSON 解码到 Go 结构体。只需定义感兴趣的字段，其余自动忽略。

```go
var titles []struct{ Title string }
json.Unmarshal(data, &titles)
```

## 流式编解码

`json.NewDecoder(r)` 从 `io.Reader` 解码，`json.NewEncoder(w)` 向 `io.Writer` 编码。

## 结构体 Tag

用 Tag 控制 JSON 字段名和行为。`omitempty` 表示零值时省略。

```go
type Movie struct {
    Title  string
    Year   int  `json:"released"`
    Color  bool `json:"color,omitempty"`
    Actors []string
}
```

## 类型映射

| JSON | Go |
|:-----|:---|
| object | struct / map[string]T |
| array | slice / array |
| string | string |
| number | int / float64 |
| boolean | bool |
| null | nil（指针/slice/map） |

---

> 来源：[Go 语言圣经 - 4.5 JSON](https://golang-china.github.io/gopl-zh/ch4/ch4-05.html)
