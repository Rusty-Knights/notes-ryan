## Apply a Trait
```rust
pub struct NewsArticle {
	pub author: String,
	pub headline: String,
	pub content: String
}

impl Summarizable for NewsArticle {} // Use default implementation

pub struct Tweet {
	pub username: String,
	pub content: String,
	pub reply: bool,
	pub retweet: bool
}

impl Summarizable for Tweet {
	fn summarize(&self) -> String { // Use custom implementation
		format!("{} {}", self.username, self.content) 
	}
}

pub trait Summarizable {
	fn summarize(&self) -> String {
		String::from("Read more..."); // Default implementation
	}
}
```

## Use a Trait Implementation
### Use Single Trait
```rust
// Basic usage, confirms that item is a specific type as well, in case we introduce item2, item3, or itemN args.
pub fn notify<T: Summarizable>(item &T) {
	println!("Summary: {}", item.summarize());
}

// With syntactic sugar, does not enforce implementing type like above
pub fn notify(item: &impl Summarizable) {
	println!("Summary: {}", item.summarize());
}
```

### Use Multiple Traits
```rust
// With + syntax
fn some_function<T: Display + Clone, U: Clone + Debug>(t: &T, u: &U) {}

// With where clause
fn some_function<T, U>(t: &T, u: &U) {
	where T: Display + Clone,
			U: Clone + Debug
}
```

### Return Trait Implementation
```rust
fn some_function() -> impl Summarizable {}

// CAUTION: Can only return one type of trait implementation. Cannot have the possiblity of returning multiple types that implement the trait. See chapter 17 for workaround.
fn some_function(toggle_type: bool) -> impl Summarizable {
	if toggle_type {
		NewsArticle {}
	}
		Tweet {} // Not allowed, must return one implementation type!
	}
}
```