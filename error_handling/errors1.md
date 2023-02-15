```rust
pub fn generate_nametag_text(name: String) -> Result<String, &'static str> {
    if name.is_empty() {
        // Empty names aren't allowed.
        Err("`name` was empty; it must be nonempty.")
    } else {
        Ok(format!("Hi! My name is {}", name))
    }
}
```