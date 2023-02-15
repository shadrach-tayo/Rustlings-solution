```rust
// Calculate `a` divided by `b` if `a` is evenly divisible by `b`.
// Otherwise, return a suitable error.
pub fn divide(a: i32, b: i32) -> Result<i32, DivisionError> {
    if b == 0 {
        return Err(DivisionError::DivideByZero);
    };

    match a % b {
        0 => Ok(a / b),
        i => Err(DivisionError::NotDivisible(NotDivisibleError {
            dividend: a,
            divisor: b,
        })),
    }
}

// Complete the function and return a value of the correct type so the test passes.
// Desired output: Ok([1, 11, 1426, 3])
fn result_with_list() -> Result<Vec<i32>, ()> {
    let numbers = vec![27, 297, 38502, 81];
    let division_results = numbers
        .into_iter()
        .map(|n| divide(n, 27))
        .map(|n| n.unwrap())
        .clone()
        .collect();
    Ok(division_results)
    // format!("{:?}", division_results)
}

// Complete the function and return a value of the correct type so the test passes.
// Desired output: [Ok(1), Ok(11), Ok(1426), Ok(3)]
fn list_of_results() -> Vec<Result<i32, ()>> {
    let numbers = vec![27, 297, 38502, 81];
    let division_results = numbers
        .into_iter()
        .map(|n| divide(n, 27))
        .map(|n| Ok(n.unwrap()))
        .clone()
        .collect();
    division_results
}
```