# Map

Map 是一个哈希表的引用，是一个无序的key/value对的集合。Map 中的 key 是唯一的且可比较的。  

key 和 value 的类型都是一致的。可以使用 len 函数检查 Map 键值对的数量。

声明语句

```
var a map[key数据类型]value数据类型
```

声明未初始化的map的值为nil，容量为 0。

```
var a map[string]int
fmt.Println(a)  // map[]
fmt.Prinln(a == nil) // true
fmt.Println(len(a))  // 0
```

声明并初始化

```
var a map[string]int = map[string]int{
    "a":25,
    "b":30,  // 逗号不能省略
}
fmt.Println(a) // map[a:25 b:30]
```

注意声明语句最后，如果最后打括号写在新的一行，最后一行元素的声明后需要加逗号，否则 Go 语言编译的时候会在最后一行加上分号，将会出现编译错误。  

先声明后初始化

```
var a map[string]int
a = map[string]int{
    "a":25,
    "b":30,  // 逗号不能省略
}
fmt.Println(a) // map[a:25 b:30]
```

Map 同样支持短语句声明

```
a := map[string]int{
    "a":25,
    "b":30,  // 逗号不能省略
}
fmt.Println(a) // map[a:25 b:30]
```

我们可以使用内置函数 make 初始化 Map

```
a := make(map[string]int)
fmt.Println(a) // map[]
```

我们可以使用下标方式访问 Map 元素和赋值，小标的值是key，返回 value 的值，如果 key 不存在返回值为 value   类型的零值。

```
a := map[string]int{
	"a":25,
	"b":30,  // 逗号不能省略
}
fmt.Println(a["a"]) // 25
fmt.Println(a["c"]) // 0
```

当我们给 Map 不存在的 key 赋值时即是往 Map 里添加了一个新的 key/value 值。往未初始化的 Map 添加元素会触发 panic，但是 执行 查找、删除、len、range时可正常执行。

```
a := map[string]int{
	"a":25,
	"b":30,  // 逗号不能省略
}
fmt.Println(a) // map[b:30 a:25]
a["c"] = 40
fmt.Println(a) // map[c:40 a:25 b:30] 注：a b c的值得顺序是随机的，后面讲。
```

内置函数 delete 用来删除 Map 元素

```
a := map[string]int{
	"a":25,
	"b":30,  // 逗号不能省略	
}	
fmt.Println(a) // map[b:30 a:25]
delete(a, "a")
fmt.Println(a) // map[b:30]
```

Map 访问不存在的值时返回零值，Go 语言提供了如下的形式判断 key 是否存在，ok 是一个 bool 值，ture 表示 key存在，false 表示不存在。

```
var a map[string]int
value, ok = a["b"]
// 配合 if 的使用
if _, ok = map["b"]; ok {
   fmt.Println(map["b"])  // 当 b 存在时会打印 b 的值
}
```

使用 range 遍历 map 的时候元素的顺序是随机的，包括我们使用 fmt.Println。  

不能对 Map 中的元素取地址，因为 Map 空间会做调整，内存会重新分配。