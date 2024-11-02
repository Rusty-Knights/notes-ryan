## Types
Standard Structs
```rust
struct User {
	username: String
	email: String
	active: bool
}
```

Tuple structs
```rust
struct RGBColor(i32, i32, i32)
struct XYZPoint(i32, i32, i32) // Not interchangable with RGBColor
```
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

## Traits
### Applying a trait
```rust
#[derive(Debug)] // apply the Debug trait
struct User {
	username: String
	email: String
	active: bool
}
```

Traits of Note:
- Debug
  For printing
```rust
println!("some_struct: {:?}", some_struct); // One line
println!("some_struct: {:#?}", some_struct); // Pretty
```
- Display
  For printing
```rust
println!("some_struct: {}", some_struct);
```