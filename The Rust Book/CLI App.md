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

## Read file
```rust
use std::fs

fn main() {
	let contents = fs::read_to_string("some_file.txt").expect("oops");
}
```