```rust
struct ColorClassicStruct {
    red: i32,
    green: i32,
    blue: i32,
}

struct ColorTupleStruct(i32, i32, i32);

fn classic_c_structs() {
    // TODO: Instantiate a classic c struct!
    let green = ColorClassicStruct {
        red: 0,
        green: 255,
        blue: 0,
    };
    // ...
}
#[test]
fn tuple_structs() {
    let green = ColorTupleStruct(0, 255, 0);
    // ...
}

fn unit_structs() {
    // TODO: Instantiate a unit-like struct!
    let unit_like_struct = UnitLikeStruct {};
    // ...
}

```
