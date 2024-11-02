## Hierarchy
- Packages
  
	- Crates
	  Sections within a package, like a directory
		- Modules
		  Code within a Crate, like a file

## Packages
- Created with `cargo new package_name`
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

