# gofmt

Go 语言在代码格式上采取了很强硬的态度，语言直接规定了代码标准格式，这样也避免了关于不同人有不同格式的无意义的争执。  

我们可以直接使用 *go* 工具的子命令 *fmt* 对指定的包或者默认的当前目录中所有的 .go 文件使用 *gofmt* 格式化。

```
$ go fmt github.com/yushuailiu/go-algorithm // 对包内的 go 文件格式化
$ go fmt // 默认对当前目录下 .go 文件格式化
```

我们也可以使用 *gofmt* 格式化，*gofmt* 命令格式如下：

```
$ gofmt -help                                                                                                     [17:37:21]
usage: gofmt [flags] [path ...]
  -cpuprofile string
    	write cpu profile to this file
  -d	display diffs instead of rewriting files
  -e	report all errors (not just the first 10 on different lines)
  -l	list files whose formatting differs from gofmt's
  -r string
    	rewrite rule (e.g., 'a[b:len(a)] -> a[b:]')
  -s	simplify code
  -w	write result to (source) file instead of stdout
```

使用 *gofmt*

```
$ gofmt main.go // 格式化 main.go 文件并把结果输出到命令行
$ gofmt -w main.go // 格式化 main.go 文件并更新到 main.go
$ gofmt -w main.go // 格式化当前目录下所有的 .go 文件
```

