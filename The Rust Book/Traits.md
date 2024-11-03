## Apply a Trait
```rust
pub struct NewsArticle {
	pub author: String,
	pub headline: String,
	pub content: String
}

pub struct Tweet {
	pub username: String,
	pub content: String,
	pub reply: bool,
	pub retweet: bool
}

pub trait Summarizable {
	fn summarize(&self) -> String {
		String::from("Read more..."); // Default implementation
	}
}
```