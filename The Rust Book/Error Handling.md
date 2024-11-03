## Panic
Prints message with backtrace, if RUST_BACKTRACE env var is 1.
```rust
panic!("message");
```

## Result Enum
Two variants: Ok and Err
```rust
let f = File.open("some_file.txt");

let f = match f {
	Ok(file) => file,
	Err(error) => panic!("Problem found when opening file");
}
```

## Expect
```rust
let f = File::open("some_file.txt").expect("Failed to open file");

// Identical to match statement
let f = match f {
	Ok(file) => file,
	Err(error) => panic!("Failed to open file");
}
```

## ? Syntax
- Will return early with the error
- Allows calling function to handle error
```rust
fn read_some_file() -> Result<io::Error> {
	let f = File::open("some_file.txt")?;
}
```
- Allows for method chaining
```rust
fn cat() -> Result<String, io::Error> {
	let mut s = String::new();
	
	// If error in opening or reading file, return early with Err result
	File::open("some_file.txt")?.read_to_string(&mut s)?; 

	// Return a success result of type string
	Ok(s)
}
```

## Reading a file
```rust
use std::fs::{self, File};

let contents = fs::read_to_string("some_file.txt"); // Return Result<String, io::Error>

// Create that file if not exists
let contents = match fs::read_to_string("some_file.txt") {
	Ok(contents) => contents,
	Err(e) => match e::kind()
}
```

## Return any type of Error
```rust
fn main -> Result<(), Box<dyn Error>> {} // wow!
```