To Shadow a variable simpling means reusing the variable name in another declaration. ``let var = 1`` => ``let var = "string"``

```rust
fn main() {
    let number = "T-H-R-E-E"; // don't change this line
    println!("Spell a Number : {}", number);
    let number = 3; // don't rename this variable
    println!("Number plus two is : {}", number + 2);
}
```