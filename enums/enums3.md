```rust
enum Message {
    // TODO: implement the message variant types based on their usage below
    Quit,
    Move(Point),
    Echo(String),
    ChangeColor((u8, u8, u8)),
}

//...

fn process(&mut self, message: Message) {
    // TODO: create a match expression to process the different message variants
    match message {
        Message::ChangeColor(color) => self.change_color(color),
        Message::Move(point) => self.move_position(point),
        Message::Echo(string) => self.echo(string),
        Message::Quit => self.quit(),
    }
}
// ...
```