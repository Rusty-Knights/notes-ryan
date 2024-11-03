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
let f = File::open("some_file.txt").expect("Failed to open");
```