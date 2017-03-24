[![Build Status](https://travis-ci.org/Xudong-Huang/generator-rs.svg?branch=master)](https://travis-ci.org/Xudong-Huang/generator-rs)
[![Build status](https://ci.appveyor.com/api/projects/status/x3mix8q57ygwqcgb/branch/master?svg=true)](https://ci.appveyor.com/project/Xudong-Huang/generator-rs/branch/master)
[![Current Crates.io Version](https://img.shields.io/crates/v/generator.svg)](https://crates.io/crates/generator)
[![Document](https://img.shields.io/badge/doc-generator-green.svg)](https://docs.rs/generator)
[![License](https://img.shields.io/crates/l/generator.svg)](https://github.com/Xudong-Huang/generator-rs)


# Generator-rs

rust generator library

you need the nightly rust compiler to compile it

use the dev version on master

```toml
[dependencies.generator]
git = "https://github.com/Xudong-Huang/generator-rs.git"
```


## Usage
```rust
#[macro_use]
extern crate generator;
use generator::Gn;

fn main() {
    let g = Gn::new_scoped(|mut s| {
        let (mut a, mut b) = (0, 1);
        while b < 200 {
            std::mem::swap(&mut a, &mut b);
            b = a + b;
            s.yield_(b);
        }
        done!();
    });

    for i in g {
        println!("{}", i);
    }
}
```

## Output
```
1
2
3
5
8
13
21
34
55
89
144
233
```

## Goals

- [x] basic send/yield with message support
- [x] generator cancel support
- [x] yield_from support
- [x] panic inside genertor support
- [x] stack size tune support
- [x] scoped static type support
- [x] basic coroutine interface support
- [ ] stable rust support


##  based on this basic library
- we can easily port python library based on generator into rust
- coroutine framework running on multi thread


## Notices

* This crate supports below platforms, welcome to contribute with other arch and platforms

    - x86_64 linux
    - x86_64 windows
