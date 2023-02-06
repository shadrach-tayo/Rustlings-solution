The ``mut`` keyword is used to mark a variable a mutable so the compiler knows that we can change the value assigned to it in the future

```rust
fn main() {
    let mut x = 3;
    println!("Number {}", x);
    x = 5; // don't change this line
    println!("Number {}", x);
}
```