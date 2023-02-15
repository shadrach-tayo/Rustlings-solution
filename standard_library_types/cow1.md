```rust
// ...
// No clone occurs because `input` is already owned.
let slice = vec![-1, 0, 1];
let mut input = Cow::from(slice);
match abs_all(&mut input) {
    // TODO
    Cow::Owned(_) => println!("I own this slice"),
    Cow::Borrowed(_) => println!("I borrowed this slice!"),
    _ => panic!("expected borrowed value"),
}
// ...
```