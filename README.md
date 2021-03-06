# Rust isatty

[![Build Status](https://travis-ci.org/dtolnay/isatty.svg?branch=master)](https://travis-ci.org/dtolnay/isatty)
[![Build Status](https://ci.appveyor.com/api/projects/status/5aq0inkv7eip6udp/branch/master?svg=true)](https://ci.appveyor.com/project/dtolnay/isatty/branch/master)
[![Latest Version](https://img.shields.io/crates/v/isatty.svg)](https://crates.io/crates/isatty)

This crate provides the following three functions:

```rust
fn stdin_isatty() -> bool
fn stdout_isatty() -> bool
fn stderr_isatty() -> bool
```

On Linux and Mac they are implemented with [`libc::isatty`]. On Windows they are
implemented with [`consoleapi::GetConsoleMode`].

[`libc::isatty`]: http://man7.org/linux/man-pages/man3/isatty.3.html
[`consoleapi::GetConsoleMode`]: https://msdn.microsoft.com/en-us/library/windows/desktop/ms683167.aspx

The `stdin_isatty` function is not yet implemented for Windows. If you need it,
please check [dtolnay/isatty#1] and contribute an implementation!

[dtolnay/isatty#1]: https://github.com/dtolnay/isatty/issues/1

<br>

## Usage

`Cargo.toml`

> ```toml
> [dependencies]
> isatty = "0.1"
> ```

`src/main.rs`

> ```rust
> extern crate isatty;
> use isatty::{stdin_isatty, stdout_isatty, stderr_isatty};
>
> fn main() {
>     println!("stdin: {}", stdin_isatty());
>     println!("stdout: {}", stdout_isatty());
>     println!("stderr: {}", stderr_isatty());
> }
> ```

<br>

#### License

<sup>
Licensed under either of <a href="LICENSE-APACHE">Apache License, Version
2.0</a> or <a href="LICENSE-MIT">MIT license</a> at your option.
</sup>

<br>

<sub>
Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in this crate by you, as defined in the Apache-2.0 license, shall
be dual licensed as above, without any additional terms or conditions.
</sub>
