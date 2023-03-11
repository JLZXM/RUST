使用cargo new创建新项目
# cargo 怎么用
## 基本语法
~~~rust
cargo new /* 创建新项目 */
cargo build /* 代码编译 */
cargo run /* 代码运行 */
~~~

## 进阶使用
直接执行编译默认会选择debug的方式进行编译，这样编译出来的应用会将debug信息都打印出来，运行起来也比较慢，所以可以选择加上 --release 选项，加快编译后的代码运行。 还可以使用cargo check 选项，快速检测代码是否能够编译通过，加快调试效率。
~~~rust
cargo build --release
cargo run --release
cargo check
~~~

## Cargo 配置
Cargo.toml 和 Cargo.lock 是 cargo 的核心文件，它的所有活动均基于此二者。
### Cargo.toml
Cargo.toml 是 cargo 特有的项目数据描述文件。它存储了项目的所有元配置信息，如果 Rust 开发者希望 Rust 项目能够按照期望的方式进行构建、测试和运行，那么，必须按照合理的方式构建 Cargo.toml。
### Cargo.lock
Cargo.lock 文件是 cargo 工具根据同一项目的 toml 文件生成的项目依赖详细清单，因此我们一般不用修改它，只需要对着 Cargo.toml 文件撸就行了。

# 定义项目依赖
使用 cargo 工具的最大优势就在于，能够对该项目的各种依赖项进行方便、统一和灵活的管理。

在 Cargo.toml 中，主要通过各种依赖段落来描述该项目的各种依赖项：

基于 Rust 官方仓库 crates.io，通过版本说明来描述
基于项目源代码的 git 仓库地址，通过 URL 来描述
基于本地项目的绝对路径或者相对路径，通过类 Unix 模式的路径来描述
这三种形式具体写法如下：
```rust
[dependencies]
rand = "0.3"
hammer = { version = "0.5.0"}
color = { git = "https://github.com/bjz/color-rs" }
geometry = { path = "crates/geometry" }
```