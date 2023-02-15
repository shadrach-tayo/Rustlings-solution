```rust
use std::num::{ParseIntError, IntErrorKind::{InvalidDigit}};

pub fn total_cost(item_quantity: &str) -> Result<i32, ParseIntError> {
    let processing_fee = 1;
    let cost_per_item = 5;
    // item_quantity.parse::<i32>().
    match item_quantity.parse::<i32>() {
        Ok(qty) => Ok(qty * cost_per_item + processing_fee),
        Err(err) => Err(err),
    }
}
```