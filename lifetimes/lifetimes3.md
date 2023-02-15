Generic lifetime annotation can be passed to structs in the format seen below
```rust
struct Book<'a> {
    author: &'a str,
    title: &'a str,
}
```