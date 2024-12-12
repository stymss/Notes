# Introduction to Rust

Rust is a systems programming language focused on speed, memory safety, and parallelism. 

---

### Basics of Rust Syntax

#### **Creating Rust Project**

To create Rust project, we can use `cargo new project_name`.

```shell
$ cargo new project_name
```

Note -> This will create a .git directory meaning git is initialised by default

```shell
$ cargo new --vcs none project_name
```

Note -> This will create the project without git initialised.


```
Above command will generate the following files:
rust_project/
│
├── Cargo.toml         # Project configuration file
└── src/
    └── main.rs        # Main source file
```

--- 

#### **Compiling and Running Code**

To compile Rust Code, we can use `rustc program_name.rs`.

```shell
$ rustc program.rs
```

`rustc` will produce a binary that can be executed

```shell
$ ./program
Hello World!
```

We can also build and run the project like this

```shell
$ cargo build # Compile your project and generate an executable.
 
$ cargo run # Execute the compiled code 
```

---

#### **Comments**
   - **Single-line Comments**: Single-line comments are created using two forward slashes (`//`).
     ```rust
     // This is a single-line comment
     ```
   - **Multi-line Comments**: Multi-line comments are written using `/*` to begin and `*/` to end.
     ```rust
     /* This is
        a multi-line comment */
     ```

   - **Documentation Comments**: To create documentation for functions, structs, or other code elements, use triple slashes `///` before the item. These comments can be processed by the Rust documentation tool (`rustdoc`).
     ```rust
     /// This function adds two numbers
     fn add(a: i32, b: i32) -> i32 {
         a + b
     }
     ```

---

#### **General Print Syntax**

To print something to the console, we can use `println!()` macro

```rust
// Print text to the console.
println!("Hello World!");
```

You can also include variables in your print statements:

```rust
let name = "Satyam";
println!("Hello, {}!", name); // Output: Hello, Satyam!
```

We can also use `Positional Arguments`.
```rust
println!("{0}, this is {1}. {1}, this is {0}", "Alice", "Bob");
```

We can have named arguments
```rust
println!("{subject} {verb} {object}",
             object="the lazy dog",
             subject="the quick brown fox",
             verb="jumps over");
```

We can only use this way of printing with types that implement `Display`,

These types implement `Display` by default.

```Built-in Types
> Numerics: Integers (i8, u8, i32, etc.) and floating points (f32, f64) display as their numeric values.
> Booleans: true or false.
> Characters (char): Displays the character literal, e.g., 'a'.
> String Types
    > str and String: Display the string’s content directly.
```

Compound Types like Structure, Enums, Options, Result, etc.. these types should implement Display manually.

```rust
fmt::Debug: Uses the {:?} marker. Format text for debugging purposes.
fmt::Display: Uses the {} marker. Format text in a more elegant, user friendly fashion.
```

For types which doesn't implement Display and Debug we need to implement these ttraits for those types.

---

#### **Debug/Display**

 All types can derive (automatically create) the `fmt::Debug` implementation. This is not true for `fmt::Display` which must be manually implemented.

 ```rust
#[derive(Debug)]
struct Person<'a> {
    name: &'a str,
    age: u8
}

fn main() {
    let name = "Peter";
    let age = 27;
    let peter = Person { name, age };

    // Pretty print
    println!("{:#?}", peter);
}

Output -> 
Person {
    name: "Peter",
    age: 27,
}
```

For `Display` we need to manually implement
```rust
use std::fmt;

struct Point {
    x: i32,
    y: i32,
}

impl fmt::Display for Point {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "({}, {})", self.x, self.y)
    }
}

let origin = Point { x: 0, y: 0 };
assert_eq!(format!("The origin is: {origin}"), "The origin is: (0, 0)");
```
