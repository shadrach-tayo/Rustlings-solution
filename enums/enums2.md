```rust
enum Message {
    // TODO: define the different variants used below
    Quit,
    Echo(String),
    Move { x: i32, y: i32 },
    ChangeColor(i32, i32, i32),
}
```