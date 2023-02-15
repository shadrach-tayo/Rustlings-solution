```rust
// ...
impl Package {
  // ...

  fn is_international(&self) -> bool {
        // Something goes here...
        self.sender_country != self.recipient_country
    }

    fn get_fees(&self, cents_per_gram: i32) -> i32 {
        // Something goes here...
        self.weight_in_grams * cents_per_gram
    }
  
}
// ...
```