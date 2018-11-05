# Slice

Slice 代表变长的特定类型的序列。底层使用数组存储，Slice 类型包含3部分：指针、长度和容量，指针是对底层数据结构的指针。  Slice 是一个序列，有长度为什么还有容量呢？可以这样理解：Go 语言中 Slice 是一个变长的序列，如果我们分配给 Slice 的数组大小和当前 Slice 里的元素一样，那么我们每次去往新的 Slice 里添加元素，我们就需要申请新的内存空间给 Slice，而容量就是为了避免这种过度的申请，当我们知道我们的 Slice 最多可以容纳多少的时候，直接声明容量大小为多少，这样就可以避免频繁的内存申请。

声明

```
var 变量名 []数据类型
```

Slice 的声明规则和数组一样，只是缺少了“数据长度”。  

未初始化的 Slice 的值为 nil，长度和容量均为 0。

```
var a []int
fmt.Println(a) // []
fmt.Println(a == nil) // true
fmt.Println(len(a)) // 0
fmt.Println(cap(a)) // 0
```

声明并初始化 Slice，初始化的元素的长度、容量为初始化列表的个数。

```
var a = []int{1, 2, 3, 4}
fmt.Println(a)
fmt.Println(len(a))
fmt.Println(cap(a))
```

初始化里列表为空的 Slice，长度容量均为 0，值不等于 nil。

```
var a = []int{}
fmt.Println(a) // []
fmt.Println(a == nil) // false
fmt.Println(len(a)) // 0
fmt.Println(cap(a)) // 0
```

slice 是不可比较的，因为 Slice 是一个指针类型，比较是无意义的，但可以自己实现不同类型的比较函数。

# make

我们可以用内置函数 make 给 Slice 赋值，make 指定 Slice 的长度和容量，容量可省略，容量默认和长度相等。

```
var a = make([]数据类型, 长度, 容量)
```

```
var a = make([]int, 5, 19)
fmt.Println(a) // [0 0 0 0 0]
fmt.Println(len(a)) // 5
fmt.Println(cap(a)) // 19

var a = make([]int, 5)
fmt.Println(a) // [0 0 0 0 0]
fmt.Println(len(a)) // 5
fmt.Println(cap(a)) // 5
```

# 切片

Slice 的底层的数据结构是数组，我们可以使用切片功能从数组或者 Slice 初始化一个新的 Slice。

```
var a [5]int = [5]int{1, 2, 3, 4, 5}
b := a[1:4]
fmt.Println(b) // [2 3 4]
```

上例子中由数组 a 初始化一个 Slice b，语法为[i:j]，其中 0<= i <= j <= len(a)，b的容量为 len(a) - i。i 可省略，省略的时默认值为0，j可省略，省略时 j = len(a)，i、j只能省略一个。b 的初始化列表为 a 的索引 i 到 索引为 j 之间不包括 j的元素，如果 i 等于 j，b 的长度为 0。a 和 b 共享同一个底层数组，即 a 的指针指向底层数组的第一个元素，b 的指针指向底层数组的第 2 个元素（元素索引从 0 开始）。修改 a 和 b 的任意一个，两者的值都会改变。

```
var a [5]int = [5]int{1, 2, 3, 4, 5}
b := a[1:4]
b[0] = 6
fmt.Println(b) // [6 3 4]
fmt.Println(a) // [1 6 3 4 5]
```

使用 Slice 初始化另外一个 Slice

```
var a = []int{1, 2, 3, 4}
b := a[2:3]
fmt.Println(b) // [3]
fmt.Println(len(b)) // 1
fmt.Println(cap(b)) // 2
b[0] = 5
fmt.Println(b) // [5]
fmt.Println(a) // [1, 2, 5, 4]
```

切片也可以用于 string，用于string的时候同样会生成一个新的字符串，但是两者的底层数据存储同样用的是一块内存空间。

# append

append函数用于向 Slice 添加元素。另外上面说到了容量，容量好像没什么用，容量真正发挥作用的地方是在 append 函数中，当我们往 Slice 里添加元素的时候，如果长度不超过容量 Slice 会继续使用原来的底层数组，如果超过容量，则 Go 语言会为 Slice 申请新的数组存放 Slice，Slice 的容量会相应的增加（容量的大小由 Go 语言决定，Go 语言会申请当前容量的两倍的长度的数组给新的 Slice）。

```
var a = []int{1, 2, 3}
fmt.Println(a) // [1, 2, 3]
fmt.Println(len(a), cap(a)) // 3 3
a = append(a, 4, 5)
fmt.Println(a) // [1, 2, 3, 4, 5]
fmt.Println(len(a), cap(a)) // 5, 6
```

