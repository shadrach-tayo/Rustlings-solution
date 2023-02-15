```rust
impl AppendBar for String {
    // TODO: Implement `AppendBar` for type `String`.
    fn append_bar(self) -> Self {
        format!("{}{}", self, "Bar")
    }
}
```
