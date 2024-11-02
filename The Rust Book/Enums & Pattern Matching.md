## Declare an Enum
Simple
```rust
enum SomeEnum {
	ValueOne,
	ValueTwo
}
```

Typed
```rust
enum Message {
	Quit,
	Move { x: i32, y: i32 },
	Write(String),
	ChangeColor(i32, i32, i32)
}
```

## Methods
```rust
impl SomeEnum {
	fn some_method() { // no &self???
		println!("hello world")
	}
}
```

## Option Enum
```rust
let some_number: Option<i32> = Some(5); // now it's nullable (kinda)
```