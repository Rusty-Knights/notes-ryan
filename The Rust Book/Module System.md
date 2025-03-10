## Hierarchy
- Packages
	- Crates
		- Modules

## Packages
- Created with `cargo new [--lib] package_name`
- A package must have at least one crate
- A package can have a max of 1 library crate, unlimited bin crates

## Crates
- Defined in Cargo.toml
- Have crate roots
	- a src file that the Rust compiler starts at when building the crate
	- implicitly are also the root module

### main.rs
- New packages with src/main.rs will have an implicit bin crate
	- Has the same name as the package
	- Uses src/main.rs as the crate root

## lib.rs
- New packages with src/lib.rs will have an implicit lib crate
	- Has the same name as the package
	- Uses src/lib.rs as the crate root

### bin/
- Each file under bin/ is a binary crate 

## Modules
- Modules can contain modules ad infinitum.
- All contents are private by default.
	- Structs must declare each attribute to be public, enums do not
```rust
mod some_mod {
	mod some_child_mod {
		fn some_func() {}
	}

	mod some_other_child_mod {
		fn some_func() {}
	}
}
```

### Calling module functions
Absolute vs Relative paths
```rust
mod front_of_house {
	pub mod hosting { // is private by default
		pub fn add_to_waitlist() {} // is private by default
	}
}

pub fn eat_at_restaurant() {
	// Absolute path
	crate::front_of_house::hosting::add_to_waitlist();

	// Relative path
	front_of_house::hosting::add_to_waitlist();
}
```

Parent and sibling functions
```rust
fn serve_order() {}

mod back_of_house {
	fn fix_incorrect_order() {
		cook_order(); // sibling
		super::serve_order(); // parent
	}

	fn cook_order() {}
}
```

Using `use`
```rust
mod front_of_house {
	pub mod hosting {
		pub fn add_to_waitlist() {}
	}
}

use self::front_of_house::hosting; // relative
use crate::front_of_house::hosting; // absolute
use self::front_of_house::hosting as h // with alias
use rand::Rng; // import vendor modules
use std::io::{self, Write}; // import vendor modules with similar paths
use std::io::* // import all from module


pub fn eat_at_restaurant() {
	hosting::add_to_waitlist();
}
```

Importing modules from adjacent files
Can define each module in separate files
```rust
// front_of_house/hosting.rs
pub fn some_other_function() {};

// front_of_house.rs
mod hosting;
pub fn some_function() {};

// main.rs
mod front_of_house;

```
