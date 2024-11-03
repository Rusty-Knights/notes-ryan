Vectors, Strings, and HashMaps
All stored on heap, so all 

## Vectors
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