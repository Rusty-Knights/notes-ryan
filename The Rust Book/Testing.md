For testing the *intent* of the code.

## Create a Simple Test
```rust
#[cfg(test)] // Marks a testing module, stands for configuration: test
mod tests {
	#[test] // Marks that a function is a test, instead of a helper function
	fn some_test() {
		assert!(true); // Will panic if false
	}
}
```

## Asserts
```rust
assert!(value); // Assert value is true
assert_eq!(value1, value2); // Assert values are equal
assert_ne!(value1, value2); // Assert values are not equal
```

### Custom failure messages
```rust
assert!(
	actual == expected, // test
	"expected {}, got {}", // failure message
	expected, // fill first placeholder in message
	actual // fill second placeholder in message
);
```

## Using Result instead of assert
```rust
#[test] 
fn some_test() -> Result<(). String> {
	let expected = 0;
	let actual = actual_func();

	match actual {
		expected => Ok(()),
		1 => Err(String::from("There was a 1!")),
		2 => Err(String::from("There was a 2!")),
		3 => Err(String::from("There was a 3!")),
	}
}
```

## Expect Panic
Without specific panic message
```rust
#[test] 
#[should_panic]
fn some_test() {
	panic("msg");
}
```

With specific panic message
```rust
#[test] 
#[should_panic(expected = "descriptive message")]
fn some_test() {
	panic("descriptive message");
}
```

### Ignoring Tests
```rust
#[test] 
#[ignore]
fn expensive_test() {
	// This could take an hour to run.
}
```
## Running Tests
### Cargo run
```bash
cargo test
```
- Launches a separate thread for each test to run in parallel.
	- CAUTION: Can cause race condition if editing same file.
- Test output, like any `println!` statements, are not printed.
	- Can see output if use `cargo test -- --show-output`.

Running one test
```bash
cargo test [pattern] # Will run all tests that contain the pattern in their name
```

Running a module
```bash
cargo test module_name::
```

Running ignored tests
```bash
cargo test -- --ignored
```

Running only integration tests
```bash
cargo test --test integration_test
```

## Integration Tests
- Unit tests are specified in the same file as production code.
- Integration tests are stored in tests/
```rust
use adder; // Makes each file in tests/ its own crate.

#[test]
fn some_test() {
	assert!(adder::some_module::some_child_module::some_func);
}
```

### Common code
- Stored in tests/common/mod.rs
- Imported with `mod common;` at the top of a file.
- Functions are used like `common::setup()`