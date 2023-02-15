The ``Arc`` struct, via the ``Clone`` implementation is used to create reference pointer to a value in memory heap while increasing the reference counter.

```rust
// ....
    let numbers: Vec<_> = (0..100u32).collect();
    let shared_numbers = numbers[0..8].to_vec(); // TODO
    let child_numbers = Arc::new(shared_numbers);
    let mut joinhandles = Vec::new();

    for offset in 0..8 {
        let child_numbers = Arc::clone(&child_numbers); // TODO
        joinhandles.push(thread::spawn(move || {
            let sum: u32 = child_numbers.iter().filter(|n| *n % 8 == offset).sum();
            println!("Sum of offset {} is {}", offset, sum);
        }));
    }
// ...
```
[For more Info](https://doc.rust-lang.org/rust-by-example/std/arc.html)