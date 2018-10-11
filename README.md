# Formatting and shortening byte slices as hexadecimal strings

This crate provides wrappers for byte slices and lists of byte slices that implement the
standard formatting traits and print the bytes as a hexadecimal string, eliding from the middle
if the length would exceed the `precision` format parameter.

```rust
use hex_fmt::{HexFmt, HexList};

assert_eq!("090a0b", &format!("{}", HexFmt(&[9u8, 10, 11])));
let nine_to_f = [9u8, 10, 11, 12, 13, 14, 15];
assert_eq!("090..0f", &format!("{:.7}", HexFmt(&nine_to_f)));
assert_eq!("090..e0f", &format!("{:.8}", HexFmt(&nine_to_f)));
assert_eq!("090a..0e0f", &format!("{}", HexFmt(&nine_to_f)));
assert_eq!("[4142, 4241]", &format!("{}", HexList(&[b"AB", b"BA"])));
```
