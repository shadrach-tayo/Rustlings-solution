We need specify a generic lifetime parameter to the ``longest`` signature because the lifetime of the return value is dependent the lifetime of both input parameters.

```rust
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
```