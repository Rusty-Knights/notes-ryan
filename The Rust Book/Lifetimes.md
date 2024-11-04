To instruct the borrow checker how long references last.
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

x and y have unknown lifetimes
```rust
// error: missing lifetime specifier. This function's return type contains a borrowed value, but the signature does not say whether it is borrowed from `x` or `y 
fn fickle(sometimes: bool, x: &str, y: &str) -> &str {
	if sometimes { x } else { y }
}
```

## Solution
```rust
// lifetime 'a is expected to be the smallest lifetime between x and y
fn fickle<'a>(sometimes: bool, x: &'a str, y: &'a str) -> &'a str { 
	if sometimes { x } else { y }
}

// otherwise, an owned type can be returned, or some other copy
fn fickle(sometimes: bool, x: &str, y: &str) -> String { 
	if sometimes { x.to_string() } else { y.to_string() }
}
```

NOTE: The lifetime of each variable introduced in the function is understood to be the scope of the function. Therefore, a lifetime in the return value means that there should be a lifetime on at least one parameter.

## In Structs
Once `value` is out of scope, `some_attr` will be a dangling reference. The lifetime 'a prevents this.
```rust
struct SomeStruct<'a> {
	some_attr: &'a str
}

fn main() {
	let value: &str = "some string";
	let some_struct = SomeStruct { some_attr: value }
}
```

## Automated Lifetimes
- Each parameter that is a reference get its own lifetime parameter.
- If there is exactly one input lifetime parameter, that lifetime is assigned to all output lifetime parameters.
- If there are multiple input lifetime parameters, but one of them is &self or &mut self, the lifetime of self is assigned to all output lifetime parameters.