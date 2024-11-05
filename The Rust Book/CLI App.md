Mini-grep
## Process Input
- .args() gives an iterator over the arguments to the app
- .collect() will store arguments in a collection. The collection type specified below is `Vec<String>`, but it could conceivably be of another type.
```rust
use std::env;

fn main() {
	let all_args: Vec<String> = env::args().collect();
	let args = all_args[1..]; // First arg is always path to executing script
}
```

## Connect main.rs to lib.rs
- Make everything that should be accessible in lib.rs public
- Add `use project_name::some_func/mod/struct` to main.rs
	- lib.rs is automatically under a crate named after the project

## Read file
.read_to_string returns a Result
```rust
use std::fs

fn main() {
	let contents = fs::read_to_string("some_file.txt").expect("oops");
}
```

### Iterate over lines
```rust
for line in content.lines() {
	// stuff
}
```

## Use env variables
```rust
use std::env;

fn main() {
	let is_set = env::var("SOME_VAR").is_err();
}
```
## Exit with a code
```rust
use std::process;

fn main() {
	process::exit(1);
}
```