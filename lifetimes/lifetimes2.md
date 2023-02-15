```rust
fn longest<'a>(x: &'a str, y: &'a str) -> String {
    if x.len() > y.len() {
        x.to_owned()
    } else {
        y.to_owned()
    }
}
```