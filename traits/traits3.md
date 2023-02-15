```rust
pub trait Licensed {
    fn licensing_info(&self) -> String {
        String::from("Some information")
    }
}
```