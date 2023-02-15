```rust
trait AppendBar {
    fn append_bar(&mut self) -> Self;
}

// TODO: Implement trait `AppendBar` for a vector of strings.
impl AppendBar for Vec<String> {
    fn append_bar(&mut self) -> Self {
        self.push(String::from("Bar"));
        self.to_vec()
    }
}
```