# for

for 是一个比较强大的流程控制语句，被用来做循环和迭代操作。  

语法格式

```
for expression1;expression2;expression3 {
    // ...
}
```

expression1 是在for循环执行前执行，expression2 是每次循环执行前执行且值为bool型表达式，expression3 每次循环结束后执行。expression1 一般用来做初始化操作，expression3 用来做迭代值变化计算，expression2 是循环条件判断。在 expression1 中声明的变量的作用域为 for 循环语句内。  

遍历一个数组例子

```
a := []int{1, 2, 3, 4, 5, 6}
for i := 0;i < len(a); i++ {
	fmt.Println(a[i])
}
```

Go 语言没有逗号操作符，需要在初始化语句初始化多个变量时可以使用多变量赋值语句。

```
a := []int{1, 2, 3, 4, 5, 6}
var sum, i int
for i, sum = 0, 0;i < len(a); i++ {
	sum += a[i]
}
fmt.Println(sum)
```

for 循环中的 expression1、expression2、expression3 都可以省略，甚至分号都可以省略。  

不需要做初始化操作时，省略 expression1 

```
a := []int{1, 2, 3, 4, 5, 6}
var sum, i int
for ;i < len(a); i++ {
	sum += a[i]
}
fmt.Println(sum)
```

不需要迭代变化时

```
a := []int{1, 2, 3, 4, 5, 6}
var sum, i int
for i, sum = 0, 0;i < len(a); {
	sum += a[i]
	i++
}
fmt.Println(sum)
```

不需要判断条件时

```
a := []int{1, 2, 3, 4, 5, 6}
var sum, i int
for i, sum = 0, 0;; i++ {
	sum += a[i]
	if i == len(a) - 1{
		break
	}
}
fmt.Println(sum)
```

只需要判断条件时（分号可以省略）

```
a := []int{1, 2, 3, 4, 5, 6}
var sum, i int
for i < len(a) {
	sum += a[i]
	i++
}
fmt.Println(sum)
```

什么都不需要时

```
a := []int{1, 2, 3, 4, 5, 6}
var sum, i int
for ;;{
	sum += a[i]
	if i == len(a) - 1{
		break
	}
	i++
}
fmt.Println(sum)
```

省略分号

```
a := []int{1, 2, 3, 4, 5, 6}
var sum, i int
for {
	sum += a[i]
	if i == len(a) - 1{
		break
	}
	i++
}
fmt.Println(sum)
```

break 用于跳出当前循环体，例如上面的只有两个分号的循环。  

continue 用于跳出当前循环。  

当多个循环嵌套时 break continue 可以配合标签跳出指定循环体。  

# range

for 配合 range 可以用来迭代 数组、Slice、Map。  

循环array

```
a := [6]int{1, 2, 3, 4, 5, 6}
for index, v := range a {
    fmt.Println(index, v)
}
```

其中 index 是数组索引，v 是数组索引为 index 的元素的值的复制。  

循环 slice 和 array 等价。  

循环 Map

```
a := map[string]int {
	"a":1,
	"b":2,
}
for key, v := range a {
	fmt.Println(index, v)
}
```

key 是 Map 的键，v 是 Map 相应 key 对应的 value 的值的复制。  

range 前的两个字段如果不需要可以使用 _ 忽略。  

```
a := [6]int{1, 2, 3, 4, 5, 6}
for _, v := range a {
    fmt.Println(v)
}
```

range 左侧的第二个值可省略

```
a := [6]int{1, 2, 3, 4, 5, 6}
for index := range a {
    fmt.Println(a[index])
}
```

