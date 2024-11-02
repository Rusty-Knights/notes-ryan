## Declaration
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
### Initialization
```rust
let some_number: Option<i32> = Some(5); // now it's nullable (kinda)
let absent_number: Option<i32> = None;
```

### Usage
```rust
let x: i8 = 5;
let y: Option<i8> = Some(4); // or None is valid as well

let sum = x + y.unwrap_or(0); // use default value if None
```

## Match Statement
All possible cases must be addressed.

```rust
enum Coin {
	Penny,
	Nickel,
	Dime,
	Quarter
}

fn process(coin: Coin) -> u8 {
	match coin {
	
	}
}
```