```rust
use std::num::{ParseIntError, IntErrorKind};
use std::str::FromStr;
#[derive(Debug, PartialEq)]
struct Person {
    name: String,
    age: usize,
}

// We will use this error type for the `FromStr` implementation.
#[derive(Debug, PartialEq)]
enum ParsePersonError {
    // Empty input string
    Empty,
    // Incorrect number of fields
    BadLen,
    // Empty name field
    NoName,
    // Wrapped error from parse::<usize>()
    ParseInt(ParseIntError),
}


// Steps:
// 1. If the length of the provided string is 0, an error should be returned
// 2. Split the given string on the commas present in it
// 3. Only 2 elements should be returned from the split, otherwise return an error
// 4. Extract the first element from the split operation and use it as the name
// 5. Extract the other element from the split operation and parse it into a `usize` as the age
//    with something like `"4".parse::<usize>()`
// 6. If while extracting the name and the age something goes wrong, an error should be returned
// If everything goes well, then return a Result of a Person object
//
// As an aside: `Box<dyn Error>` implements `From<&'_ str>`. This means that if you want to return a
// string error message, you can do so via just using return `Err("my error message".into())`.

impl FromStr for Person {
    type Err = ParsePersonError;
    fn from_str(s: &str) -> Result<Person, Self::Err> {
        if s.is_empty() {
            return Err(ParsePersonError::Empty);
        }
        
        let mut params = s.split(",").into_iter();
        
        let name = match params.next() {
            Some(n) => String::from(n),
            None => return Err(ParsePersonError::NoName),
        };

        if name.is_empty() {
            return Err(ParsePersonError::NoName);
        }

        let age = match params.next() {
            Some(n) => match n.parse::<usize>() {
                Ok(r) => r,
                Err(err) => return Err(ParsePersonError::ParseInt(err)),
            },
            None => return Err(ParsePersonError::BadLen),
        };

        match params.next() {
            Some(_) => Err(ParsePersonError::BadLen),
            None => Ok(Person { name, age }),
        }
    }
}

fn main() {
    let p = "Mark,20".parse::<Person>().unwrap();
    println!("{:?}", p);
}
```