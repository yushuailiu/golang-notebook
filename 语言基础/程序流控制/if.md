# if

if 是条件控制语句，满足某种情况就执行，否者不执行。Go 语言 if 后的表达式不要括号，且表达式的值必须是 bool 值。

```
x := 2
if x >1 {
    fmt.Println(x) // 2
}
```

Go 中 if 最强大的是 if 条件表达式中可以声明一个临时变量，该临时变量的值在 if 作用域内有效。

```
x :=2 
if y:=3;x>1 {
    fmt.Println(x, y) // 2 3
}
```

if 多分支的情况

```
if x > 1 {
   fmt.Println("x>1")
} else if x > 2 {
    fmt.Println("x>2")
} else {
    fmt.Println("<=1")
}
```

else if 中同样可以声明一个临时变量。

```
x :=3
if x<1 {
	fmt.Println(x, y)
} else if z := 4; x >2 {
	fmt.Println(z) // 4
}
```

在一个包含多分支的 if else 语句中，前面 if 声明的变量在后面的 *else if* 或则 *else* 中也是有效的作用域区间。

```
x :=-1
if y:=3;x>1 {
	fmt.Println(x, y)
} else if z := 4; x >2 {
	fmt.Println(z,y)
} else {
	fmt.Println(x,y,z) // -1 3 4
}
```