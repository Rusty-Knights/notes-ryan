## The Problem
Lifetimes protects against dangling references.
```rust
let r;

{
	let x = 5;
	r = &x; // error: x does not live long enough
}
// At this point, the stack frame for the block above is deallocated.
// x is deallocated along with it.
// r is pointed to deallocated memory.

println!("r: {}", r); // r is a dangling reference
```

```rust
fn fickle(sometimes: bool) -> &str { // error: missing lifetime specifier. This function's return type contains a borrowed value, but the signature does not say whether it is borrowed from `x` or `y 
	if sometimes { x } else { y }
}
```