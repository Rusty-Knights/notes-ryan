## Cargo
Run a project
```bash
cargo run
```

## Types
String
- A string type that is compatible with functions for string transformations

&str
- A string type that is used mostly used as a reference.
- Can be converted to a String type by calling .to_string()
- Functions typically take &str arguments and return String values

string literal
- "some string"
- has different functions available, like colors .red() function
- stored directly in binary
- are fixed in size

tuples
- Mass assignment `let (channel, sub_count) = ("Let's Get Rusty!", 100_000)`
- Random access `some_tuple.0`

array
- Must have length, e.g. `[0; 8]` creates 8 instances of 0

## Syntax
!
A function followed by a bang is a macro, which expands to a larger function.

_
- Can be used as a , in a long number

const
- Must have a type annotation
```rust
const SOME_VALUE: u32 = 100_000;
```

return
- Not necessary. Can be last expression in block, no semi-colon needed.

loop
- Runs until `break;`
- Can return a value, like a function
```rust
let value = loop {
	break 10;
}
```

for loop
```rust
for item in arr.iter() {
	// statement
}

for item in 1..4 {
	//statement
}
```

## Terms
- statement = do NOT return a value
- expression = return a value

## Type Conversion
### parse()
Convert a string to the type specified in the variable declaration.
```rust
let value: u32 = some_string.parse();
```
### Shadowing
```rust
let x = 5;
let x = "some string"
```

### String::from()
Allocates memory to heap 👍
```rust
String::from("string literal")
```