# 🚨 Deprecated: π-crust Macros

This repository has been deprecated.

Piecrust Macros is no longer maintained, as all functionality has been consolidated and improved in [Dusk Forge](https://github.com/HDauven/dusk-forge).

[![Repository](https://img.shields.io/badge/github-piecrust%20macros-blueviolet?logo=github)](https://github.com/HDauven/piecrust-macros)
[![Documentation](https://img.shields.io/badge/docs-piecrust%20macros-blue?logo=rust)](https://docs.rs/piecrust-macros/)

`piecrust-macros` is a macro library designed to simplify the development of smart contracts for Dusk's [Piecrust virtual machine](https://github.com/dusk-network/piecrust). It provides macros to automatically generate the boilerplate code required for interfacing smart contracts with the Piecrust VM.

## Usage

The main feature of `piecrust-macros` is the `#[contract]` attribute macro. This macro automatically generates wrapper functions required for interfacing with the Piecrust VM, reducing boilerplate code in your project.

Add `piecrust_macros` as a dependency to your contract project:
```sh
cargo add piecrust_macros
```

To use the macro, import it into your Rust smart contract and annotate your contract's implementation with #[contract]:

```rust
#![no_std]

use piecrust_macros::contract;

/// Struct that describes the state of the Counter contract
pub struct Counter {
    value: i64,
}

/// State of the Counter contract
static mut STATE: Counter = Counter { value: 0xfc };

#[contract]
impl Counter {
    /// Read the value of the counter
    pub fn read_value(&self) -> i64 {
        self.value
    }

    /// Increment the value of the counter by 1
    pub fn increment(&mut self) {
        let value = self.value + 1;
        self.value = value;
    }
}
```

With #[contract], the macro automatically generates the necessary wrapper functions for each public method in the impl block you want to expose.


## Release History

To see the release history for this crate, please see the [CHANGELOG](./CHANGELOG.md) file.

## License

This code is licensed under the Mozilla Public License Version 2.0 (MPL-2.0). Please see the [LICENSE](./LICENSE) for further details.

## Contribute

If you want to contribute to this project, feel free to open an issue, fork the repository and open a pull request.
