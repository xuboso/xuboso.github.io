---
title: goroutine
date: 2024-12-05 21:57:07
tags:
  - go
---

### goroutine

how to limit goroutines use semaphore

[https://bostonc.dev/blog/go-semaphore](https://bostonc.dev/blog/go-semaphore)

[https://gist.github.com/jboursiquot/ef53edb815fe18c8160dbe8504dd9d60](https://gist.github.com/jboursiquot/ef53edb815fe18c8160dbe8504dd9d60)

```go
var (
  concurrency = 5
  semaChan = make(chan struct{}, concurrency)
)

func doWork(item int) {
  semaChan <- struct{}{} // block while full
  go func() {
    defer func() {
      <-semaChan // read releases a slot
    }()
    // work
    log.Println(item)
    time.Sleep(1 * time.Second)
  }()
}

func main(){
  for i := 0; i <= 1000; i++ {
    doWork(i)
  }
}
```

[https://medium.com/deep-golang/8-python-performance-tips-i-discovered-after-years-of-coding-in-golang-764375658d90](https://medium.com/deep-golang/8-python-performance-tips-i-discovered-after-years-of-coding-in-golang-764375658d90)

[https://medium.com/deep-golang/5-go-concurrency-patterns-i-wish-id-picked-up-sooner-b1b7dae6d71e](https://medium.com/deep-golang/5-go-concurrency-patterns-i-wish-id-picked-up-sooner-b1b7dae6d71e)

[https://medium.com/@ahamrouni/mastering-concurrency-in-go-from-goroutines-to-semaphores-123fdd150213](https://medium.com/@ahamrouni/mastering-concurrency-in-go-from-goroutines-to-semaphores-123fdd150213)

### 参考

[著名的 one million websockets](https://www.freecodecamp.org/news/million-websockets-and-go-cc58418460bb/)

[https://github.com/eranyanay/1m-go-websockets](https://github.com/eranyanay/1m-go-websockets)

[https://www.bomberbot.com/golang/scaling-to-a-million-websockets-with-go/](https://www.bomberbot.com/golang/scaling-to-a-million-websockets-with-go/)

[https://awesome-go.com/goroutines/](https://awesome-go.com/goroutines/)

[https://ofeng.org/posts/goroutine-pool/](https://ofeng.org/posts/goroutine-pool/)

[https://go.libhunt.com/categories/493-goroutines](https://go.libhunt.com/categories/493-goroutines)

[https://medium.com/deep-golang](https://medium.com/deep-golang)
