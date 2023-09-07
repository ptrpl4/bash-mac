# 🏃♂ Go

#### links

tour - [https://go.dev/tour](https://go.dev/tour)

examples - [https://gobyexample.com/](https://gobyexample.com/)

Language Specification - [https://go.dev/ref/spec](https://go.dev/ref/spec)

sandbox - [https://go.dev/play/](https://go.dev/play/)

### Basics

./hello.go

```go
package main

import "fmt"
// line comment
func main() {
    fmt.Println("hello everyone")
}
/*
General comment
Thanks for reading!
*/
```

running/building

```bash
$ go run hello.go
hello everyone
$ go build hello.go
$ ls
hello	hello.go
$ ./hello
hello everyone
```

