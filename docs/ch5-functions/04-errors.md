---
layout: default
title: 5.4 错误
parent: 5. 函数
nav_order: 4
---

# 5.4 错误

Go 将错误视为**预期结果之一**，通过返回值而非异常机制处理。

## 错误类型

`error` 是内置接口。`nil` 表示成功，非 `nil` 表示失败。失败原因唯一时可用 `bool`，原因多样时用 `error`。

## 五种错误处理策略

**1. 传播错误**（最常用）

```go
doc, err := html.Parse(resp.Body)
if err != nil {
    return nil, fmt.Errorf("parsing %s as HTML: %v", url, err)
}
```

**2. 重试**（偶发性错误，限制次数/超时）

```go
for tries := 0; time.Now().Before(deadline); tries++ {
    _, err := http.Head(url)
    if err == nil { return nil }
    time.Sleep(time.Second << uint(tries))
}
```

**3. 终止程序**（仅在 main 中）

```go
log.Fatalf("Site is down: %v\n", err)
```

**4. 仅记录日志**

```go
log.Printf("ping failed: %v; networking disabled", err)
```

**5. 忽略错误**（需注释说明）

```go
os.RemoveAll(dir) // 忽略错误，系统会定期清理
```

## 编码风格

先处理错误，再写正常逻辑：

```go
f, err := os.Open(name)
if err != nil {
    return err
}
// 正常逻辑
```

## EOF

`io.EOF` 表示读到文件末尾，可直接比较：

```go
if err == io.EOF {
    break
}
```

---

> 来源：[Go 语言圣经 - 5.4 错误](https://golang-china.github.io/gopl-zh/ch5/ch5-04.html)
