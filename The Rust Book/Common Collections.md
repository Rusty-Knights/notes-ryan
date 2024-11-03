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
Cannot change a value to which there is already an immutable reference. When the immutable referenced is printed, it is expected that the underlying value has not changed.

Pushing a new element might trigger a expansion, where the underlying array is replaced by a duplicate with double the capacity and values are copied over. In that case, the original immutable reference would be pointed to an erroneous section of memory.
```rust
let mut v = vec![1, 2, 3, 4, 5];

let third = &v[2]; // Borrows as immutable

v.push(6); // Cannot borrow v as mutable if it is already borrowed as immutable.

println!("immutable ref: {}", third); // Uses immutable
```

## String
### Initialization
```rust
let s: String = String::from("Hello World!");
let s: &str = "Hello World!"
let s: String = "Hello World!".to_string()
```

### Concatenation
```rust
let s: String = String::from("foo");
s.push_str("bar"); // push a &str
s.push('!'); // push a char

let s1 = String::from("Hello, ");
let s2 = String::from("world!");
let s3 = s1 + &s2; // Moves ownership of s1 to s3. Can no longer use s1.
```