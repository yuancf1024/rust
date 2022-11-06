# Rust by Example

[toc]

## 介绍

Rust是一种现代系统编程语言，重点是安全，速度和并发。它通过在不使用垃圾回收的情况下确保内存安全来实现这些目标。

例如，Rust（RBE）是一个可运行的示例的集合，这些示例说明了各种Rust概念和标准库。要从这些示例中获得更多信息，请不要忘记在本地安装Rust并查看官方文档。此外，对于好奇，您还可以查看此站点的源代码。

现在让我们开始吧！
- Hello World - Start with a traditional Hello World program. 从传统的Hello World项目开始。

- Primitives - Learn about signed integers, unsigned integers and other primitives. 了解有符号整数，无签名的整数和其他原语。

- Custom Types - struct and enum. 结构和枚举。

- Variable Bindings - mutable bindings, scope, shadowing. 可突变的绑定，范围，阴影。

- Types - Learn about changing and defining types. 了解更改和定义类型。

- Conversion

- Expressions

- Flow of Control - if/else, for, and others.

- Functions - Learn about Methods, Closures and High Order Functions. 了解方法，闭包和高阶函数。

- Modules - Organize code using modules 使用模块组织代码

- Crates - A crate is a compilation unit in Rust. Learn to create a library. Crates是Rust的编译单元。学习创建库。

- Cargo - Go through some basic features of the official Rust package management tool. 浏览官方Rust软件包管理工具的一些基本功能。

- Attributes - An attribute is metadata applied to some module, crate or item. 属性应用于某些模块，crate或项目。

- Generics - Learn about writing a function or data type which can work for multiple types of arguments. 了解编写可以适用于多种类型参数的函数或数据类型。

- Scoping rules - Scopes play an important part in ownership, borrowing, and lifetimes. 范围在所有权，borrowing和生命周期中起着重要的作用。

- Traits - A trait is a collection of methods defined for an unknown type: Self 特征是为未知类型定义的方法集合：自我

- Macros

- Error handling - Learn Rust way of handling failures. 学习处理故障的Rust方法。

- Std library types - Learn about some custom types provided by std library. 了解STD库提供的一些自定义类型。

- Std misc - More custom types for file handling, threads. 更多用于文件处理的自定义类型，线程。

- Testing - All sorts of testing in Rust. Rust中的各种测试。

- Unsafe Operations

- Compatibility

- Meta - Documentation, Benchmarking. 文档，基准测试。


## 01-Hello World

**编译** : `rustc hello.rs`

**运行** : `./hello`

```rust
fn main() {
    // 当调用二进制文件时执行此处的表达式

    // 打印文本到终端
    println!("Hello World!"); // println! 是一个宏命令
    println!("I'm a Rustacean!");
}
```

### 1.1 注释

Any program requires comments, and Rust supports a few different varieties:

- Regular comments which are ignored by the compiler:
  - `// Line comments which go to the end of the line.`
  - `/* Block comments which go to the closing delimiter. */`
- Doc comments which are parsed into HTML library documentation:
  - `/// Generate library docs for the following item.`
  - `//! Generate library docs for the enclosing item.`

### 1.2 格式化打印

Printing is handled by a series of `macros` defined in `std::fmt` some of which include:

- `format!:` write formatted text to `String`
- `print!:` same as `format!` but the text is printed to the console (io::stdout).
- `println!:` same as `print!` but a newline is appended.
- `eprint!:` same as `print!` but the text is printed to the standard error (io::stderr).
- `eprintln!:` same as `eprint!` but a newline is appended.

All parse text in the same fashion. As a plus, Rust checks formatting correctness at compile time.

```rust

```


`std::fmt` contains many `traits` which govern the display of text. The base form of two important ones are listed below:

- `fmt::Debug:` Uses the `{:?}` marker. Format text for debugging purposes.
- fmt::Display: Uses the `{}` marker. Format text in a more elegant, user friendly fashion.

Here, we used `fmt::Display` because the std library provides implementations for these types. To print text for custom types, more steps are required.

Implementing the `fmt::Display` trait automatically implements the `ToString` trait which allows us to `convert` the type to `String`.


