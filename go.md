不同于其他语言，go中没有项目的说法，只有包, 其中有两个重要的路径，GOROOT 和 GOPATH

Go开发相关的环境变量如下：

GOROOT：GOROOT就是Go的安装目录，（类似于java的JDK）
ubuntu apt install 在  /usr/lib/go-1.18/  或者 /usr/share/go-1.18/
GOPATH：GOPATH是我们的工作空间,保存go项目代码和第三方依赖包

GOPATH可以设置多个，其中，第一个将会是默认的包目录，
使用 go get 下载的包都会在第一个path中的src目录下，
使用 go install时，在哪个GOPATH中找到了这个包，就会在哪个GOPATH下的bin目录生成可执行文件

linux下 export | grep GOPATH 发现在  $HOME/go

例如安装个 goplantuml
go get github.com/jfeliu007/goplantuml/parser
go install github.com/jfeliu007/goplantuml/cmd/goplantuml@latest
增加了 $HOME/go/pkg/mod/github.com/jfeliu007/goplantuml@v1.6.1
和 ~/go/bin/goplantuml

goplantuml [-recursive] path/to/gofiles path/to/gofiles2
