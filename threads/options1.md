```rust
 // TODO: Complete the function body - remember to return an Option!
match time_of_day {
    0 => Some(0),
    1..=21 => Some(5),
    22..=24 => Some(0),
    _ => None
}

#[test]
fn raw_value() {
    // TODO: Fix this test. How do you get at the value contained in the Option?
    let icecreams = maybe_icecream(12).unwrap();
    assert_eq!(icecreams, 5);
}
```
