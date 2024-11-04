Mini-grep
## Process Input
- .args() gives an iterator over the arguments to the app
- .collect() will store arguments in a collection. The collection type is specified below as Vec<
```rust
use std::env;

fn main() {
	let args: Vec<String> = env::args().collect();
}
```