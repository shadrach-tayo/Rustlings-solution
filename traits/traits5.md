```rust
// YOU MAY ONLY CHANGE THE NEXT LINE
fn some_func<T>(item: T) -> bool 
where 
    T: SomeTrait + OtherTrait
{
    item.some_function() && item.other_function()
}
```