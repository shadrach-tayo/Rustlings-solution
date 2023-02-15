```rust
for fruit in fruit_kinds {
    // TODO: Put new fruits if not already present. Note that you
    // are not allowed to put any type of fruit that's already
    // present!
    if (!basket.contains_key(&fruit)) {
        basket.insert(fruit, 2);
        }
}
```