```rust
fn trim_me(input: &str) -> String {
    input.trim().to_string()
}

fn compose_me(input: &str) -> String {
    format!("{input}{}", " world!")
}

fn replace_me(input: &str) -> String {
    input.replace("cars", "balloons")
}
```