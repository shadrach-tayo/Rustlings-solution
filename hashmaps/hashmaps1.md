To access public funtions in a module we use the ``use`` statement to bring a module into scope as seen below

```rust
let mut basket = HashMap::new(); // TODO: declare your hash map here.

// Two bananas are already given for you :)
basket.insert(String::from("banana"), 2);

// TODO: Put more fruits in your basket here.
basket.insert("apple".to_string(), 2);
basket.insert("mango".to_string(), 1);
```