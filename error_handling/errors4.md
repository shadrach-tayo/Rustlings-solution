```rust
impl PositiveNonzeroInteger {
    fn new(value: i64) -> Result<PositiveNonzeroInteger, CreationError> {
        // Hmm...? Why is this only returning an Ok value?
        if value == 0 {
            return Err(CreationError::Zero);
        }
        if value < 0 {
            return Err(CreationError::Negative);
        }
        Ok(PositiveNonzeroInteger(value as u64))
    }
}
```