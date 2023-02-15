```rust
// TODO: Make this an if let statement whose value is "Some" type
if let Some(word) = optional_target {
    assert_eq!(word, target);
}

// TODO: make this a while let statement - remember that vector.pop also adds another layer of Option<T>
// You can stack `Option<T>`'s into while let and if let
while let Some(integer) = optional_integers.pop() {
    assert_eq!(integer.unwrap(), range);
    range -= 1;
}
```