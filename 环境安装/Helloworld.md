我们照常以”Hello world"做为案例来演示一个最简单的 Go 程序，并分析讲解其构成。

[github.com/yushuailiu/golang-notebook-code/chapter1/demo0](https://github.com/yushuailiu/golang-notebook-code/chapter1/demo0)

```
package main

import "fmt"

func main() {
	fmt.Println("Hello world!")
}
```

代码结构分析  

代码第一行是包声明，在 Go 程序里任何一个源码文件都属于一个包，而 main 包是一个特殊的包，main 包表明一个源码程序目标是编译成一个可独立执行的程序，而程序的入口函数就是 main 函数。  

第三行是包引入语句，有时候我们的程序需要依赖其他的包来完成某些功能，那么就需要引入第三方包。我们这里使用了 Go 标准库里的 *fmt* 包用来打印输出，所以我们引入了该包。  

第五行是我们程序的入口函数 main 函数的声明。

第六行我们调用了*fmt*包的*Println*函数打印输出字符串“Hello world!"。

Go 语言是一个编译型语言，也就是说 Go 程序源码会被 编译成机器指令。所以要运行一个 Go 程序首先需要编译成二进制可执行程序，然后才可以执行。而 *go* 命令提供了一个 *run* 子命令，这个命令会把一个或者多个 Go 源码文件编译成一个可执行文件并放在一个临时目录里，然后执行并删除临时文件。

```
$ go run helloworld.go
Hello world!
```

当我们需要程序重复运行的时候，我们可以把源码打包成一个可执行的二进制程序。

```
$ go build -o helloworld helloworld.go
$ ls
helloworld    helloworld.go
```

*go*  命令的子命令 *build* 用来编译打包源码程序成一个可独立执行的二进制程序，参数 *-o* 用来指定生成二进制程序的名。  

执行 helloworld 程序可以看到同样的输出。

```
$./helloworld
Hello world!
```

