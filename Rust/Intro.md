# Introduction to Rust

Rust is a systems programming language focused on speed, memory safety, and parallelism. 

---

### Basics of Rust Syntax

#### 1.  **Creating Rust Project**

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

#### 2.  **Compiling and Running Code**

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

#### 3. **Comments**
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

#### 4. **General Print Syntax**

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

---

