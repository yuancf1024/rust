# Rust权威指南の学习笔记

[toc]

## 日志

1. 2022-11-06 第1章
2. 

## 第1章 入门指南

### Linux环境安装Rust

**终端输入命令安装rust：**

```shell
curl https://sh.rustup.rs -sSf | sh
```

```shell
root@LAPTOP-22O3I9E3:/home/yuancf1024/rust# curl https://sh.rustup.rs -sSf | sh
info: downloading installer

Welcome to Rust!

This will download and install the official compiler for the Rust
programming language, and its package manager, Cargo.

Rustup metadata and toolchains will be installed into the Rustup
home directory, located at:

  /root/.rustup

This can be modified with the RUSTUP_HOME environment variable.

The Cargo home directory is located at:

  /root/.cargo

This can be modified with the CARGO_HOME environment variable.

The cargo, rustc, rustup and other commands will be added to
Cargo's bin directory, located at:

  /root/.cargo/bin

This path will then be added to your PATH environment variable by
modifying the profile files located at:

  /root/.profile
  /root/.bashrc
  /root/.zshenv

You can uninstall at any time with rustup self uninstall and
these changes will be reverted.

Current installation options:


   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable (default)
               profile: default
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
>1

info: profile set to 'default'
info: default host triple is x86_64-unknown-linux-gnu
info: syncing channel updates for 'stable-x86_64-unknown-linux-gnu'
info: latest update on 2022-11-03, rust version 1.65.0 (897e37553 2022-11-02)
info: downloading component 'cargo'
  6.5 MiB /   6.5 MiB (100 %)   3.8 MiB/s in  1s ETA:  0s
info: downloading component 'clippy'
info: downloading component 'rust-docs'
 18.8 MiB /  18.8 MiB (100 %)   3.7 MiB/s in  5s ETA:  0s
info: downloading component 'rust-std'
 30.0 MiB /  30.0 MiB (100 %)   2.3 MiB/s in 16s ETA:  0s
info: downloading component 'rustc'
 56.2 MiB /  56.2 MiB (100 %)   2.7 MiB/s in 23s ETA:  0s
info: downloading component 'rustfmt'
info: installing component 'cargo'
info: installing component 'clippy'
info: installing component 'rust-docs'
 18.8 MiB /  18.8 MiB (100 %)   9.1 MiB/s in  1s ETA:  0s
info: installing component 'rust-std'
 30.0 MiB /  30.0 MiB (100 %)  14.4 MiB/s in  2s ETA:  0s
info: installing component 'rustc'
 56.2 MiB /  56.2 MiB (100 %)  16.6 MiB/s in  3s ETA:  0s
info: installing component 'rustfmt'
info: default toolchain set to 'stable-x86_64-unknown-linux-gnu'

  stable-x86_64-unknown-linux-gnu installed - rustc 1.65.0 (897e37553 2022-11-02)


Rust is installed now. Great!

To get started you may need to restart your current shell.
This would reload your PATH environment variable to include
Cargo's bin directory ($HOME/.cargo/bin).

To configure your current shell, run:
source "$HOME/.cargo/env"
```

**终端运行命令来让配置立即生效**

```shell
source /home/yuancf1024/.cargo/env
```

**安装最新稳定版本**

```shell
rustup default stable

# 显示信息
info: syncing channel updates for 'stable-x86_64-unknown-linux-gnu'
714.2 KiB / 714.2 KiB (100 %) 335.4 KiB/s in  1s ETA:  0s
info: latest update on 2022-11-03, rust version 1.65.0 (897e37553 2022-11-02)
info: downloading component 'cargo'
  6.5 MiB /   6.5 MiB (100 %)   3.2 MiB/s in  1s ETA:  0s
info: downloading component 'clippy'
info: downloading component 'rust-docs'
 18.8 MiB /  18.8 MiB (100 %)   2.9 MiB/s in  8s ETA:  0s
info: downloading component 'rust-std'
 30.0 MiB /  30.0 MiB (100 %)   3.4 MiB/s in 11s ETA:  0s
info: downloading component 'rustc'
 56.2 MiB /  56.2 MiB (100 %)   2.1 MiB/s in 22s ETA:  0s
info: downloading component 'rustfmt'
  4.3 MiB /   4.3 MiB (100 %)   2.6 MiB/s in  1s ETA:  0s
info: installing component 'cargo'
info: installing component 'clippy'
info: installing component 'rust-docs'
 18.8 MiB /  18.8 MiB (100 %)   9.6 MiB/s in  1s ETA:  0s
info: installing component 'rust-std'
 30.0 MiB /  30.0 MiB (100 %)  15.3 MiB/s in  1s ETA:  0s
info: installing component 'rustc'
 56.2 MiB /  56.2 MiB (100 %)  16.8 MiB/s in  3s ETA:  0s
info: installing component 'rustfmt'
info: default toolchain set to 'stable-x86_64-unknown-linux-gnu'

  stable-x86_64-unknown-linux-gnu installed - rustc 1.65.0 (897e37553 2022-11-02)
```

**更新与卸载**

```shell

# 显示安装版本
rustc --version

# 更新
rustup update

$ rustc 1.65.0 (897e37553 2022-11-02)

# 卸载
rustup self uninstall

# 查阅rust官方文档
rustup doc
```


### Hello, World!

**编译运行**

```shell
# 编译
rustc main.rs

# 运行
./main
```

```rust
fn main() {
    println!("Hello, world!");
}
```

```shell
$ rustc main.rs
$ ls
main  main.rs
$ ./main
Hello, world!
```

### Hello, Cargo!

**创建项目**

```shell
# 创建新项目
cargo new hello_cargo

# 进入项目路径
cd hello_cargo

# 构建任务
cargo build

# 同时完成编译和运行任务
cargo run

# 快速检查当前代码能否通过编译
cargo check

# 以Release模式构建任务 (准备好发布自己的项目)
cargo build --release

# 想要对代码运行效率进行基准测试(可执行程序在target/release目录)
cargo run --release

# 快速clone项目并执行构建操作
$ git clone someurl.com/someproject
$ cd someproject
$ cargo build
```