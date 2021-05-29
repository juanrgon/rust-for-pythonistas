# Rust for Pythonistas

A Rust tutorial designed for Python developers

## Variables

### Declaring a variable

**Python**

In Python, you declare a variable in one way:

```python
x = 1
```

**Rust**

In Rust, you must use the `let` keyword to declare a new variable:

```rust
// You can declare a variable with an initial value. When doing
let x = 1;

println!("The value of x is: {}", x);

// You can also declare a variable, without an initial value.
// If you do so, you have to specify the type of the variable.
let x i32;
```

### Modifying a Variable

**Python**

In Python, modifying a variable is very straight-forward:

```python
x = 1
x = 2
```

**Rust**

In Rust, variables are immutable by default. To allow a variable to be mutable, you must use the `mut` keyword when declaring:

```rust
// banana is immutable
let banana = "yellow";

// apple is mutable, so it's value can change
let mut apple = "red";
apple = "green";
```

Although Rust variables are immutable by default, you are allowed to re-declare a variable. This concept is known as `shadowing`:

```rust
let x = 5;
let x = 6;
let x = x + 1;
let x = "pineapple";  // the type of a variable can be changed when shadowing
```

## Constants

**Python**

In Python there is isn't a formal definition of a constant. However, it is common to name variables in all-caps to hint to others that a variable shouldn't change:

```python
# this variable can be modified, but the all-caps suggests that it should be treated as a constant
RIGHT_ANGLE = 90
```

**Rust**

In Rust, constants can be declared with the `const` keyword:

```rust
const RIGHT_ANGLE: u16 = 90;
```

`const` and variables that haven't been declared as mutable differ in these ways:

- the type of a `const` must be annotated
- `const`s can be declared in any scope, including the global scope, which makes them useful for values that many parts of code need to know about.
- `const`s may be set only to a constant expression, not the result of a function call or any other value that could only be computed at runtime.

## Data Types

### Booleans

In Python there are only two `bool` types `True` and `False`.

Similarly, in Rust, there are only two `bool` types: `true` and `false`.

### Integers

**Python**

In Python all integers are of type `int`.

The amount of memory an `int` takes up is dynamic, i.e. `int`s start at a size between 16 bytes and 32 bytes (the exact value depends on your version of Python), but very large ints are supported and will automatically use more memory.

**Rust**

In Rust there are signed integers: `i8`, `i16`, `i32`, `i64`, which correspond to 1, 2, 4, 8 bytes respectively.

You can also define unsigned integers: `u8`, `u16`, `u32`, `u64`.

Which integer type you want to use is dependent on the problem that you are solving, but to help you decide, here is a table of the min and max values possible with each type:

| **type** | min                        | max                        |
|----------|----------------------------|----------------------------|
| i8       | -127                       | 127                        |
| i16      | -32,767                    | 32,767                     |
| i32      | -2,147,483,647             | 2,147,483,647              |
| i64      | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807  |
| u8       | 0                          | 255                        |
| u16      | 0                          | 65,535                     |
| u32      | 0                          | 4,294,967,295              |
| u64      | 0                          | 18,446,744,073,709,551,615 |

If you’re unsure which integer type you need, Rust’s defaults are generally good choices, and integer types default to i32: this type is generally the fastest, even on 64-bit systems.

### Floats

**Python**

In Python all integers are of type `float`.

Like `int`s, floats can be arbitrarily large but are usually between 16 and 32 bytes in size.

**Rust**

In rust floats are either `f32` for 32-bits, or `f64` for 64 bits.

```rust
let x = 2.0; // f64

let y: f32 = 3.0; // f32
```

### Strings

In Python, a `str` is a sequence of characters. You can iterate over the characters in a string, but each character returned is itself a string:

```python
assert all(isinstance(c, str) for c in 'hello')
```

In Rust, a `str` is a sequence of `char` types:

```rust
let x = 'a'; // a char
let y = "hello"; // a string
```

A `char` is 4 bytes and represents a Unicode Scalar Value.

### Iterables

**Python**

In Python, the built-in iterable types are `list` and `tuple`.
