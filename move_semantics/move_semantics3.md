```rust
fn main() {
    let vec0: Vec<i32> = Vec::new();

    let mut vec1 = fill_vec(&mut vec0[..].to_vec());

    println!("{} has length {} content `{:?}`", "vec1", vec1.len(), vec1);

    vec1.push(88);

    println!("{} has length {} content `{:?}`", "vec1", vec1.len(), vec1);
}

fn fill_vec(vec: &mut Vec<i32>) -> Vec<i32> {
    vec.push(22);
    vec.push(44);
    vec.push(66);

    vec.to_vec()
}
```