```rust
pub fn factorial(num: u64) -> u64 {
    // Complete this function to return the factorial of num
    // Do not use:
    // - return
    // Try not to use:
    // - imperative style loops (for, while)
    // - additional variables
    // For an extra challenge, don't use:
    // - recursion
    match num {
        0..=1 => 1,
        i => i * factorial(num - 1)
    }
    // Execute `rustlings hint iterators4` for hints.
}

```
