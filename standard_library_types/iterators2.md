```rust
// Step 1.
// Complete the `capitalize_first` function.
// "hello" -> "Hello"
pub fn capitalize_first(input: &str) -> String {
    let mut c = input.chars();
    match c.next() {
        None => String::new(),
        Some(first) => format!("{}{}", first.to_uppercase(), &input[1..].to_owned()),
    }
}

// Step 2.
// Apply the `capitalize_first` function to a slice of string slices.
// Return a vector of strings.
// ["hello", "world"] -> ["Hello", "World"]
pub fn capitalize_words_vector(words: &[&str]) -> Vec<String> {
    words
        .iter()
        .map(|w| w[0..1].to_uppercase() + &w[1..])
        .collect()
    // words.to_owned()
}

// Step 3.
// Apply the `capitalize_first` function again to a slice of string slices.
// Return a single string.
// ["hello", " ", "world"] -> "Hello World"
pub fn capitalize_words_string(words: &[&str]) -> String {
    words
        .iter()
        .map(|w| w[0..1].to_uppercase() + &w[1..])
        .collect::<Vec<String>>()
        .join("")
}
```