```rust
fn main () {
    let my_fav_fruits = vec!["banana", "custard apple", "avocado", "peach", "raspberry"];

    let mut my_iterable_fav_fruits = my_fav_fruits.into_iter();   // TODO: Step 1

    assert_eq!(my_iterable_fav_fruits.next(), Some("banana"));
    assert_eq!(my_iterable_fav_fruits.next(), Some("custard apple"));     // TODO: Step 2
    assert_eq!(my_iterable_fav_fruits.next(), Some("avocado"));
    assert_eq!(my_iterable_fav_fruits.next(), Some("peach"));     // TODO: Step 3
    assert_eq!(my_iterable_fav_fruits.next(), Some("raspberry"));
    assert_eq!(my_iterable_fav_fruits.next(), None);     // TODO: Step 4
}
```