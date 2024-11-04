For testing the *intent* of the code.

## Create a Simple Test
```rust
#[cfg(test)] // Marks a testing module
mod tests {
	#[test] // Marks that a function is a test, instead of a helper function
	fn some_test() {
		assert_eq!(2 + 2, 4);
	}
}
```

## 