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
- Is stored in UTC-8
- Each character could be 1, 2, 3, or 4 bytes
- &str[0] wouldn't work since the first byte may not be a full char

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
let s3 = format!("{}{}", s1, s2); // No ownership is given
let s3 = s1 + &s2; // Moves ownership of s1 to s3. Can no longer use s1.

```

### Iteration
```rust
use unicode_segmentation::UnicodeSegmentation;

// Bytes
for b in "hello".bytes() {
	println!("{}", b);
}

// Scalar values
for c in "hello".chars() {
	println!("{}", c);
}

// Grapheme clusters
for g in "hello".graphemes(true) {
	println!("{}", g);
}
```

## HashMaps
- Key/Value Pairs of any type
- `use std::collections::HashMap`

### Initialization
```rust
use std::collections::HashMap

let mut scores = HashMap::new();

scores.insert(String::from("blue"), 10);
scores.insert(String::from("Yellow"), 50);

let blue_score: Option<i32> = scores.get(String::from("blue"));
```

### .
```rust
scores.insert(String::from("blue"), 10); // Set blue to 10
scores.insert(String::from("blue"), 20); // Will overwrite blue to 20

scores.entry(String::from("yellow")).or_insert(30); // Will set yellow to 30
scores.entry(String:;from("yellow")).or_insert(40); // Will leave yellow at 30
```