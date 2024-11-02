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
		email,  // No need to say email: email
		username,
		active: true
	}
}
```

Spread fill struct fields
```rust
struct User {
	username: String
	email: String
	active: bool
}

fn main() {
	user2 = User {
		email: String::from("user1@email.com")
		username: String::from("user1")
		active: true
	}

	user2 = User {
		email: String::from("user2@email.com")
		username: String::from("user2")
		..user1 // instead of active: true
	}
}
```