```rust
use std::ops::Mul;

// Obtain the number of bytes (not characters) in the given argument.
// TODO: Add the AsRef trait appropriately as a trait bound.
fn byte_counter<T: AsRef<str>>(arg: T) -> usize 
{
    arg.as_ref().as_bytes().len()
}

// Obtain the number of characters (not bytes) in the given argument.
// TODO: Add the AsRef trait appropriately as a trait bound.
fn char_counter<T: AsRef<str>>(arg: T) -> usize {
    arg.as_ref().chars().count()
}

// Squares a number using as_mut().
// TODO: Add the appropriate trait bound.
fn num_sq<T: AsMut<u32> + AsRef<u32>>(arg: &mut T) {
    // let mut value = *arg.as_mut();
    // TODO: Implement the function body.
    *arg.as_mut() = *arg.as_ref() * *arg.as_ref() ;
}

```