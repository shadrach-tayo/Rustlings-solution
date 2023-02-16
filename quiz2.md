```rust
mod my_module {
    use super::Command;
    pub const BAR: &'static str = "bar";
    pub fn transformer(input: Vec<(&str, Command)>) -> Vec<String> {
        // TODO: Complete the output declaration!
        let mut output: Vec<String> = vec![];

        for (string, command) in input.iter() {
            println!("input {string}");
            match command {
                Command::Append(pos) => output.push(format!("{}{}", string, BAR.repeat(*pos))),
                Command::Trim => output.push(string.trim().to_string()),
                Command::Uppercase => output.push(string.to_uppercase())
            };
        }
        output
    }
}
```