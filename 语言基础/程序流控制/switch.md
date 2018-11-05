# switch

switch 用来处理多条件分支的情况。

```
switch expr {
    case expr1:
    	do something1
    case expr2:
    	do something2
    default:
    	do something3
}
```

expr 必须和 expr1、expr2 的值类型相同

```
i := 1
switch i {
    case 1:
    	fmt.Println(1)
    case 2,3:
    	fmt.Println(2)
    default:
    	fmt.Println("default")
}
```

case 后的表达式可以是多个值，使用逗号隔开，匹配其中给一个值即执行该 case 下的语句。  

当所有 case 值都不匹配的时候，执行 default 下的语句。  

匹配到某一个 case 之后，执行完即跳出 switch，如果需要继续执行紧接着后面的 case 下的语句，需要使用 fallthrough 关键字。  

expr可以省略，省略的时候 case 后的表达式值类型布尔值，为真则匹配

```
i := 1
switch {
case i == 1:
	fmt.Println(1)
case i == 2:
	fmt.Println(2)
default:
	fmt.Println("default")
}
```

