Go 语言支持以下系统

- Linux
- FreeBSD
- Mac OS X
- windows

安装包下载地址：https://golang.org/dl/  

## Linux/Mac OS X/FreeBSD

各个系统中都会有程序管理的工具去安装 Go ，比如 Mac 的 homebrew、Centos 的 yum 等。我们这里只讲一下使用二进制包的安装方式。  

1. 根据自己的系统下载二进制包
2. 将二进制包解压到 /usr/local 目录
3. 添加 /usr/local/go/bin 目录到 PATH 环境变量

## windows

windows 系统直接下载相应的安装程序点击安装即可，一般会安装到 c:\Go 目录下，把 c:\Go\bin 目录添加到 PATH 环境变量中即可。

## 测试

当我们安装完成后可以使用如下命令测试如果有类似输出即表示安装成功。

```
$ go version
go version go1.11 darwin/amd64
```

## GOROOT GOBIN GOPATH

我们安装好 go 之后需要设置另外两个环境变量：GOROOT、GOPATH。  

GOROOT 设置为 go 的安装目录即上面的 /usr/local/go或则 c:\Go。

GOPATH 设置一个文件目录并且不能和 GOROOT 一样，该目录下会包含3个子文件夹：src、bin、pkg。src 会包含我们下载的三方库的源码以及存放我们自己项目的源码，bin 目录是用来保存我们编译成的执行程序，pkg 用来保存编译之后的包文件（注：每一个 Go 项目有两类类型，一种是可编译成可执行文件的，这种便以结果放在 bin 目录下，第二种是包文件，这种不会编译成可执行程序，只为其他项目提供函数等，编译结果会放在 pkg 目录下）。  GOPATH 可以包含多个，但是推荐只设置一个。

如果我们想要全局可以执行 GOPATH 目录下的 bin 目录的可执行程序，我们也需要把 bin 目录添加到 PATH 环境变量中。或者我们也可以设置另外一个环境变量 GOBIN，这个变量的值是一个目录，用于指定 go 生成的可执行文件不放在 GOPATH 下的 bin 中而放在一个新的的目录下。