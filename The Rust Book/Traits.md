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
pub fn notify(item: &impl Summarizable) {
	println!("Summary: {}", item.summarize());
}
```