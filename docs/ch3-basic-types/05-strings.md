---
layout: default
title: 3.5 字符串
parent: 3. 基础数据类型
nav_order: 5
---

# 3.5 字符串

## 基本特性

字符串是**不可变**的字节序列。`len(s)` 返回字节数（非字符数），`s[i]` 访问第 i 个字节，`s[i:j]` 切片，`+` 拼接。支持 `==`、`<` 比较（逐字节）。子串切片与原串共享底层内存。

## 字面值

双引号支持转义（`\n`、`\t`、`\xhh`、`\ooo` 等）。反引号 `` ` `` 为原生字符串，无转义，可跨行，适合正则、HTML 模板、JSON 等。

## Unicode 与 UTF-8

Go 源文件和字符串默认 UTF-8 编码。ASCII 占 1 字节，中文等占 2-4 字节：

```go
s := "Hello, 世界"
len(s)                        // 13（字节）
utf8.RuneCountInString(s)     // 9（字符）
```

`range` 循环自动按 UTF-8 解码为 `rune`；`[]rune(s)` 转为码点序列，`string(r)` 转回。

## 字符串与 []byte

`[]byte(s)` 拷贝为可变字节切片，`string(b)` 拷贝回不可变字符串。频繁拼接用 `bytes.Buffer` 避免重复分配。

## 常用包

- **strings**：查询、替换、拆分、合并
- **bytes**：同 strings 但操作 `[]byte`，含 `Buffer` 类型
- **strconv**：字符串与数值互转
- **unicode / unicode/utf8**：字符分类、UTF-8 编解码

## 字符串与数字转换

```go
strconv.Itoa(123)                // "123"
strconv.Atoi("123")              // 123, err
strconv.FormatInt(123, 2)        // "1111011"
strconv.ParseInt("123", 10, 64)  // 123, err
fmt.Sprintf("%d", 123)           // "123"
```

---

> 来源：[Go 语言圣经 - 3.5 字符串](https://golang-china.github.io/gopl-zh/ch3/ch3-05.html)
