- Vectors, Strings, and HashMaps
- Have dynamic sizes
- Are all stored on heap, so are dropped once they fall out of scope

## Vectors
### Initialization
```rust
// New Vector
let v: Vec<i32> = Vec::new();

// New mutable Vector with elements
let mut v2: Vec<i32> = Vec::new();
v2.push(1);
v2.push(2);
v2.push(3);

// New vector with elements, oneline, type inferred
let v3 = vec![1, 2, 3];
```

### Access Elements
```rust
let v = vec![1, 2, 3, 4, 5];

// CAUTION: could reference element out of bounds
let third = &v[2];

// SAFE
match v.get(2) {
	Some(third) => println!("The third element is {}", third),
	None => println!("There is no third element.")
}
```

### Common error
```rust
let mut v = vec![1, 2, 3, 4, 5];
let third = &v[2];
v.push(6); // 
```