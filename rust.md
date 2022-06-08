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
