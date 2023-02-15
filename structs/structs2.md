```rust
//...
 fn your_order() {
    let order_template = create_order_template();
    // TODO: Create your own order using the update syntax and template above!
    let your_order = Order {
        name: "Hacker in Rust".to_string(),
        count: 1,
        ..order_template
    };
    // ...
 }
```