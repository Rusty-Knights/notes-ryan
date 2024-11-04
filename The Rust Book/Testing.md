For testing the *intent* of the code.

## Create a Simple Test
```rust
#[cfg(test)] // Marks a testing module
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
#[cfg(test)]
#[test] 
#[should_panic(expected = "descriptive message")]
fn some_test() {
	panic("descriptive message");
}
```