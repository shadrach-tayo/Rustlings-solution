```rust
// YOU MAY ONLY CHANGE THE NEXT LINE
fn compare_license_types(software: impl Licensed, software_two: impl Licensed) -> bool {
    software.licensing_info() == software_two.licensing_info()
}
```