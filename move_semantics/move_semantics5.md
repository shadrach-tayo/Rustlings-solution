```rust
fn main() {
    let mut x = 100;
    let y = &mut x;
    let x = 1200;
    *y += 100;
    // z += 1000;
    assert_eq!(x, 1200);
}
```