---
layout: default
title: 5.3 多返回值
parent: 5. 函数
nav_order: 3
---

# 5.3 多返回值

Go 函数可以返回多个值，最常见的模式是返回结果和错误信息。

## 基本用法

```go
func findLinks(url string) ([]string, error) {
    resp, err := http.Get(url)
    if err != nil {
        return nil, err
    }
    return visit(nil, doc), nil
}

links, err := findLinks(url)   // 接收全部
links, _ := findLinks(url)     // 忽略错误
```

## 多返回值传递

```go
func findLinksLog(url string) ([]string, error) {
    log.Printf("findLinks %s", url)
    return findLinks(url)  // 直接转发
}
```

## 命名返回值

```go
func Size(rect image.Rectangle) (width, height int)
func Split(path string) (dir, file string)
```

## 裸返回（bare return）

所有返回值命名时，`return` 可省略操作数：

```go
func CountWordsAndImages(url string) (words, images int, err error) {
    resp, err := http.Get(url)
    if err != nil {
        return    // 等价于 return 0, 0, err
    }
    words, images = countWordsAndImages(doc)
    return        // 等价于 return words, images, nil
}
```

裸返回能减少重复，但多处 return 时降低可读性，不宜过度使用。

---

> 来源：[Go 语言圣经 - 5.3 多返回值](https://golang-china.github.io/gopl-zh/ch5/ch5-03.html)
