# goto

Go 语言中可以声明一个标签，而 goto 可以用来控制程序执行跳转到标签的位置。  

如下使用 goto 实现的一个循环

```
x := 20
test:
if x > 15 {
    fmt.Println("goto")
    goto test
}
```

