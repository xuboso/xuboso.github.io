---
title: go string and []byte
date: 2024-11-22 20:41:57
tags:
  - go
---

先看[]byte的数据结构

```go
type slice struct {
  data uintptr
  len int
  cap int
}
```

string的数据结构

```go
type string struct {
  data uintptr
  len int
}
```

String不可变，[]byte可变

String默认是UTF-8编码, []byte没有

由于String类型是不可变的，如果经常需要拼接字符等，可以使用`strings.Builder`方法

[]byte适合二进制传输，尤其适合文件，网络传输，因为网络就是按字节传输的

[]byte转换string

```go
data := []byte{72, 101, 108, 108, 111, 44, 32, 87, 111, 114, 108, 100, 33}
text := string(data)

data := "Hello, World!"
b := []byte(data)     // string转换[]byte
s := string(b)        // []byte转换string
```

[]rune是int32类型，默认占四个字节，即使是ASCII字符一样，所以比string和[]byte占用的内存空间更大。

> Use strings for simplicity and Unicode support, 
bytes for mutability and versatility, 
and runes for character-level operations.


[https://medium.com/@tyler_brewer2/bits-bytes-and-byte-slices-in-go-8a99012dcc8f](https://medium.com/@tyler_brewer2/bits-bytes-and-byte-slices-in-go-8a99012dcc8f)

[https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)

[https://www.codingexplorations.com/blog/understanding-strings-bytes-and-runes-in-go-advantages-and-disadvantages](https://www.codingexplorations.com/blog/understanding-strings-bytes-and-runes-in-go-advantages-and-disadvantages)

[https://100go.co/20-slice/](https://100go.co/20-slice/)

[https://syslog.ravelin.com/byte-vs-string-in-go-d645b67ca7ff](https://syslog.ravelin.com/byte-vs-string-in-go-d645b67ca7ff)

[https://www.ekwbtblog.com/entry/2023/03/20/080011](https://www.ekwbtblog.com/entry/2023/03/20/080011)