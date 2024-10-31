## Stack
- Fixed size
- Stores stack frames
	- Store variables within that scope
	- Variables are deallocated with frame
- Accessing data is faster

## Heap
- Dynamic in size
- Variables are also dynamic in size, e.g. String, Vec
- Stack frames have pointers to heap data
- Accessing data is slower

## Ownership Rules
1. Each value in Rust has a variable that's called its owner.
2. There can only be one owner at a time.
3. When the owner goes out of scope, the value will be dropped.

## Move
- A move is when a heap variable is given a new owner.
```rust
let s1 = String::from("literal");
let s2 = s1;
println!("{}", s1);

// runtime error, since s1 has been moved
```
- Simple types (like integers, booleans), and characters are copied on the stack instead of moved, when passed to functions or to variables
- A move can happen when passing a variable to a function.
```rust
let s = String::from("literal");
takes_ownership(s);
```

## References
### Read-only References
- A pointer to the value being referenced.
	- For a heap variable: a stack pointer -> to a stack pointer -> heap data
- Technically belong to new owner being passed to, will be deallocated
```rust
fn some_function(s1: &String) {}
let s2 = &s1;
```

##

### Mutable References
- Only one mutable reference per datum
- Only can exist for mutable variables