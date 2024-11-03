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
