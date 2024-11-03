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
// Allows for using ints and floats for either x or y
// CAUTION: no traits limit the generics here
struct Point<T, U> {
	x: T,
	y: U
}

impl<V, W> Point<V, W> {
	fn x(&self) -> &V {
		&self.x
	}
}

// How do I define a y method for implementations besides f64?
impl Point<f64, f64> {
	fn y(&self) -> f64 {
		self.y
	}
}
```

## With Enums
```rust
enum Option<T> {
	Some(T),
	None
}

enum Result<T, E> {
	Ok(T),
	Error(E)
}
```

##