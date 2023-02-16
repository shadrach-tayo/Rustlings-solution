```rust
use std::convert::{TryFrom, TryInto};

#[derive(Debug, PartialEq)]
struct Color {
    red: u8,
    green: u8,
    blue: u8,
}

// We will use this error type for these `TryFrom` conversions.
#[derive(Debug, PartialEq)]
enum IntoColorError {
    // Incorrect length of slice
    BadLen,
    // Integer conversion error
    IntConversion,
}


// Your task is to complete this implementation
// and return an Ok result of inner type Color.
// You need to create an implementation for a tuple of three integers,
// an array of three integers, and a slice of integers.
//
// Note that the implementation for tuple and array will be checked at compile time,
// but the slice implementation needs to check the slice length!
// Also note that correct RGB color values must be integers in the 0..=255 range.

// Tuple implementation
impl TryFrom<(i16, i16, i16)> for Color {
    type Error = IntoColorError;
    fn try_from(tuple: (i16, i16, i16)) -> Result<Self, Self::Error> {
        // let (red, green, blue) = tuple;
        
        let red = match tuple.0 {
            0..=255 => tuple.0,
            _ => return  Err(IntoColorError::IntConversion),
        };
        
        let green = match tuple.1 {
            0..=255 => tuple.1,
            _ => return  Err(IntoColorError::IntConversion),
        };
        
        let blue = match tuple.2 {
            0..=255 => tuple.2,
            _ => return  Err(IntoColorError::IntConversion),
        };

        return Ok(Color {
            red: red as u8,
            green: green as u8,
            blue: blue as u8,
        });
    }
}

// Array implementation
impl TryFrom<[i16; 3]> for Color {
    type Error = IntoColorError;
    fn try_from(arr: [i16; 3]) -> Result<Self, Self::Error> {
        if arr.len() != 3 {
            return Err(IntoColorError::BadLen);
        }
        let mut input = arr.into_iter();

        let red = match input.next() {
            Some(i) => match i {
                0..=255 => *i as u8,
                _ => return  Err(IntoColorError::IntConversion),
            },
            _ =>  return  Err(IntoColorError::IntConversion),
        };
        
        let green = match input.next() {
            Some(i) => match i {
                0..=255 => *i as u8,
                _ => return  Err(IntoColorError::IntConversion),
            },
            _ =>  return  Err(IntoColorError::IntConversion),
        };
        
        let blue = match input.next() {
            Some(i) => match i {
                0..=255 => *i as u8,
                _ => return  Err(IntoColorError::IntConversion),
            },
            _ =>  return  Err(IntoColorError::IntConversion),
        };        

        return Ok(Color {
            red: red,
            green: green,
            blue: blue,
        });
    }
}

// Slice implementation
impl TryFrom<&[i16]> for Color {
    type Error = IntoColorError;
    fn try_from(slice: &[i16]) -> Result<Self, Self::Error> {
        let mut input = slice.to_owned();

        if input.len() != 3 {
            return Err(IntoColorError::BadLen);
        }

        let mut input = input.iter_mut();

        let red = match input.next() {
            Some(i) => match i {
                0..=255 => *i as u8,
                _ => return  Err(IntoColorError::IntConversion),
            },
            _ =>  return  Err(IntoColorError::IntConversion),
        };
        
        let green = match input.next() {
            Some(i) => match i {
                0..=255 => *i as u8,
                _ => return  Err(IntoColorError::IntConversion),
            },
            _ =>  return  Err(IntoColorError::IntConversion),
        };
        
        let blue = match input.next() {
            Some(i) => match i {
                0..=255 => *i as u8,
                _ => return  Err(IntoColorError::IntConversion),
            },
            _ =>  return  Err(IntoColorError::IntConversion),
        };

        return Ok(Color {
            red: red,
            green: green,
            blue: blue,
        });
    }
}

fn main() {
    // Use the `try_from` function
    let c1 = Color::try_from((183, 65, 14));
    println!("{:?}", c1);

    // Since TryFrom is implemented for Color, we should be able to use TryInto
    let c2: Result<Color, _> = [183, 65, 14].try_into();
    println!("{:?}", c2);

    let v = vec![183, 65, 14];
    // With slice we should use `try_from` function
    let c3 = Color::try_from(&v[..]);
    println!("{:?}", c3);
    // or take slice within round brackets and use TryInto
    let c4: Result<Color, _> = (&v[..]).try_into();
    println!("{:?}", c4);
}
```