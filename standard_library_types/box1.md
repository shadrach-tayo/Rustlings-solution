A ``Box`` is a smart pointer to a heap allocated value of type T, it can be used to wrap recursive types using that othersise would not be stored on the stack.

```rust
#[derive(PartialEq, Debug)]
pub enum List {
    Cons(i32, Box<List>),
    Nil,
}


pub fn create_empty_list() -> List {
    // todo!()
    List::Nil
}

pub fn create_non_empty_list() -> List {
    // todo!()
    List::Cons(1, Box::new(List::Nil))
}
```
[For more Info](https://doc.rust-lang.org/rust-by-example/std/box.html)