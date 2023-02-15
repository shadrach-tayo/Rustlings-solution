```rust
#[derive(Debug)]
enum GenericVar<'a> {
    Int(u32),
    Str(&'a str),
    Bool(bool),
    Byte(u8),
}

fn main() {
    let mut shopping_list: Vec<GenericVar> = Vec::new();
    shopping_list.push(GenericVar::Str("milk"));
}
```