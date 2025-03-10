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
#[derive(Debug)]
enum UsState {
	Alabama,
	Alaska,
	Arizona,
	// ...
}

enum Coin {
	Penny,
	Nickel,
	Dime,
	Quarter(UsState)
}

fn process(coin: Coin) -> u8 {
	match coin {
		Coin::Penny => {
			println!("Lucky penny!");
			1
		}
		Coin::Nickel => 5,
		Coin::Dime => 10,
		Coin::Quarter(state: UsState) => {{
			println!("A quarter from {:?} State!", state);
			25
		}
	}
}
```

Can use Option Enum
```rust
fn plus_one(num: Option<i32>) -> Option<i32> {
	match x {
		None => None,
		Some(i) => Some(i + 1) // Must return Option enum type
	}
}
```

Can do nothing
```rust
let some_value = Some(3);
match some_value {
	Some(3) => println!("three"),
	_ => ()
}

// Could be rewritten with if/let syntax. Is not exaustive, only covers conditional given
// Meant to be read backwards: if some_value equals Some(3).
// Yes, the single equals is correct :|
if let Some(3) = some_value {
	println!("three");
}
```