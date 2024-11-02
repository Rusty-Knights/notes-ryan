## Hierarchy
- Packages
  Created with `cargo new package_name`
	- Crates
	  Sections within a package, like a directory
		- Modules
		  Code within a Crate, like a file

## Crates
- Defined in Cargo.toml
- New packages already have an implicit bin crate
	- Has the same name as the package
	- Uses src/main.rs as the crate root
- Has a crate root
	- a src file that the Rust compiler starts at when building the crate
	- implicitly is also the root module

