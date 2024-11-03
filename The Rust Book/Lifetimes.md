## The Problem
Lifetimes protects against dangling references.
```rust
let r;

{
	let x = 5;
	r = &x;
}
// At this point, the stack frame for the block above is deallocated.
// x is deallocated along with it.
// r is 

println!("r: {}", r); // r is a dangling reference
```