## Syntax
Field init shorthand
```rust
struct User {
	username: String
	email: String
	active: bool
}

fn build_user(email: String, username: String) -> User {
	User {
			email,
		username,
		active: true
	}
}
```