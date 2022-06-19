https://dev.to/davidadewoyin/top-rust-cargo-commands-2b70

### 基本命令
cargo build
cargo test
cargo tree
cargo search
cargo install
cargo uninstall
cargo run --example hello
``` shell
# 修改cargo源为国内
vim ~/.cargo/config
[source.crates-io]
replace-with = 'ustc'

[source.ustc]
registry = "git://mirrors.ustc.edu.cn/crates.io-index"
# 如果 ~/.gitconfig 中设置了http_proxy 可能出现
spurious network error (2 tries remaining): [35] SSL connect error (OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to crates-io.proxy.ustclug.org:443 )
错误
```


### 错误 
#### error[E0554]: `#![feature]` may not be used on the stable release channel
``` shell
rustup install nightly
cargo +nightly build

rustup toolchain install nightly
rustup default nightly
```

### 查找不再使用的依赖项
``` shell
cargo install cargo-udeps --locked
cargo +nightly udeps
```

### 注释
1. 行注释是二个反斜杠//
2. 文档注释是三个反斜杠///  , //!  和  /*!   !*/，可以用cargo doc来生成html说明文档。
>  //!  和  /*!   !*/  使用位置有限制

### 命名规范
1. 变量标识符和函数标识：符官方要求就是小写加下划线拼接的方式，  a_b
2. 常量：尽量遵循全大写加下划线拼接的方式。 A_B
3. 结构体： 大驼峰命名法  ABit

### struct | enum
枚举有多种可能性。结构只有一种可能的“类型”。在数学上，我们说结构是产品类型，枚举是产品的总和。如果您只有一种可能性，请使用结构。例如，空间中的一个点总是三个数字。它永远不会是字符串、函数或其他东西。所以它应该是一个包含三个数字的结构。另一方面，如果您正在构建一个数学表达式，它可能是（例如）一个数字或两个由运算符连接的表达式。它有多种可能性，所以它应该是一个枚举。

简而言之，如果结构有效，请使用结构。Rust 可以围绕它进行优化，并且任何阅读您的代码的人都会更清楚该值应该被视为什么。

Rust 中的枚举更像联合而不是结构，尽管枚举可以有结构变体。

枚举的大小等于任何单个变体的最大大小 + 一些用于编码该枚举的特定实例是哪个变体的标识符的空间。这个变种的数据只是一堆字节，程序不知道如何解释，除非它有标识符。

当你说“枚举中只有一件事”时，也许你在想一个枚举的大小与其所有变体的大小相加，并且标识符选择要查看的枚举的哪个“部分”。不是这种情况。对于枚举的每个变体，都在查看和读取/写入相同的数据。这没关系，因为枚举一次只能有一个变体。
