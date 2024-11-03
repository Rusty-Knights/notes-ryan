## Standard Usage
```rust
// PartialOrd and Copy are traits
// PartialOrd means T must be ordered
// Copy means T must be copyable, aka must be a primitive type (int, bool, char)
fn max<T: PartialOrd + Copy>(values: Vec<T>) -> T {
	let mut max: T = values[0];

	for value: T in values {
		if value > max {
			max = value;
		}
	}

	max
}
```

## With Structs
```rust

```