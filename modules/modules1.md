To access public funtions in a module we use the ``use`` statement to bring a module into scope as seen below

```rust
fn main() {
    use sausage_factory::*;
    sausage_factory::make_sausage();
}
```