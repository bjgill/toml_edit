# toml_edit

[![Build Status](https://img.shields.io/travis/ordian/toml_edit/master.svg?label=linux%20%26%20osx)](https://travis-ci.org/ordian/toml_edit)
[![Build Status](https://ci.appveyor.com/api/projects/status/github/ordian/toml_edit?svg=true)](https://ci.appveyor.com/project/ordian/toml-edit/branch/master)
[![codecov](https://codecov.io/gh/ordian/toml_edit/branch/master/graph/badge.svg)](https://codecov.io/gh/ordian/toml_edit)
[![crates.io](https://img.shields.io/crates/v/toml_edit.svg)](https://crates.io/crates/toml_edit)
[![docs](https://docs.rs/toml_edit/badge.svg)](https://docs.rs/toml_edit/badge.svg)
[![Join the chat at https://gitter.im/toml_edit/Lobby](https://badges.gitter.im/a.svg)](https://gitter.im/toml_edit/Lobby)


This crate allows you to parse and modify toml
documents, while *mostly* preserving comments, spaces and
relative order or items.

Things it does not preserve include:
1. Spaces in headers, e.g. `[ ' a ' .  b ]` will be represented as [' a '.b]
2. Children tables before parent table (tables are reordered).
3. Scattered array of tables (tables are reordered).

`toml_edit` is primarily tailored for [cargo-edit](https://github.com/killercup/cargo-edit/) needs.

## Example

```rust
extern crate toml_edit;

use toml_edit::Document;

fn main() {
    let toml = r#"
      "hello" = 'toml!' # comment
      ['a'.b]
    "#;
    let doc = toml.parse::<Document>();
    assert!(doc.is_ok());
    assert_eq!(doc.unwrap().to_string(), toml);
}
```

## License

Licensed under either of

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or http://apache.org/licenses/LICENSE-2.0)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any additional terms or conditions.
