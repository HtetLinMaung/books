# Rust Basics for the Experienced Programmer

## Variables and Data Types

In Rust, as in many programming languages, variables are used to store data that can be used and manipulated throughout a program. Rust is a statically-typed language, which means the type of a variable must be known at compile time. This chapter delves into the intricacies of variables and data types in Rust.

1. `Declaring Variables`:

- By default, variables in Rust are immutable, meaning their values cannot be changed once they're set.

```rs
let x = 5;
```

- To make a variable mutable, use the `mut` keyword:

```rs
let mut y = 7;
y = 10; // This is valid because y is mutable.
```

2. `Data Types`:

Rust has several built-in data types, broadly categorized into:

- `Scalar Types`: Represent a single value.

  - `Integers`: Numbers without a fractional component. Examples include `i8`, `i16`, `u32`, and `u64`, where `i` stands for signed and `u` for unsigned.
  - `Floating-Point`: Numbers with a fractional component. Rust has two floating-point types: `f32` and `f64`.
  - `Boolean`: Has two possible values, `true` or `false`.
  - `Character`: Represents a single Unicode character and is denoted by `char`.

- `Compound Types`: Group multiple values into one type.
  - `Tuples`: A fixed-length collection of values of possibly different types.
  ```rs
  let tup: (i32, f64, char) = (500, 6.4, 'Z');
  ```
  - `Arrays`: A fixed-length collection of values of the same type.
  ```rs
  let arr: [i32; 5] = [1, 2, 3, 4, 5];
  ```

3. `Type Inference`:

- Rust is adept at inferring the type of a variable based on the value assigned to it and how the variable is used.

```rs
let x = 3;      // Rust infers that `x` is of type i32
let y = 3.0;    // Rust infers that `y` is of type f64
```

4. `Shadowing`:

- In Rust, you can declare a new variable with the same name as a previous variable, effectively shadowing the previous variable.

```rs
let x = 5;
let x = x + 1;  // Here, the first `x` is shadowed by the second `x`.
```

5. `Constants`:

- Constants are always immutable and must have their type annotated. They can be declared in any scope, including the global scope.

```rs
const MAX_POINTS: u32 = 100_000;
```

6 `Differences Between Variables and Constants`:

- Unlike variables, constants cannot be marked with the mut keyword.
- Constants can be declared in any scope, including the global scope.
- Constants can only be set to a constant expression, not the result of a function call or any other value computed at runtime.

In conclusion, understanding variables and data types is foundational to Rust programming. They form the building blocks upon which more complex data structures and algorithms are constructed. Rust's emphasis on immutability, type safety, and clear syntax ensures that developers can write efficient and error-free code.

## Control Flow: Conditionals and Loops

Control flow determines the order in which code is executed. Rust provides a variety of constructs to control this flow, allowing developers to specify conditions under which certain blocks of code are run and to repeat blocks of code multiple times. This chapter explores the conditional and looping constructs in Rust.

1. `Conditionals`:

- `if Expressions`:
  Rust's `if` expressions allow you to branch your code based on conditions.
  ```rs
  let number = 5;
  if number < 10 {
    println!("The number is less than 10.");
  } else if number == 10 {
    println!("The number is 10.");
  } else {
    println!("The number is greater than 10.");
  }
  ```
- `Using if in a let Statement`:
  You can assign a value to a variable based on a condition.
  ```rs
  let condition = true;
  let number = if condition {
    5
  } else {
    6
  };
  ```

2. `Loops`:

- `loop`:
  The `loop` keyword provides an infinite loop. Use this when you want to loop until a specific condition is met.
  ```rs
  loop {
    println!("This will print indefinitely!");
  }
  ```
- `while`:
  The `while` loop runs while a condition is true.
  ```rs
  let mut number = 3;
  while number != 0 {
    println!("{}!", number);
    number -= 1;
  }
  ```
- `for`:
  The `for` loop is used to loop over elements of a collection, such as an array.
  ```rs
  let arr = [10, 20, 30, 40, 50];
  for element in arr.iter() {
    println!("The value is: {}", element);
  }
  ```
- `Range in for Loops`:
  You can use the `..` syntax to generate a range of values.
  ```rs
  for number in (1..4).rev() {
    println!("{}!", number);
  }
  ```

3. `Controlling Loop Execution`:

- `break`:
  Immediately exits the loop.
  ```rs
  loop {
    println!("Looping...");
    break;  // This will exit the loop after one iteration.
  }
  ```
- `continue`:
  Skips the rest of the loop iteration and begins the next iteration.
  ```rs
  for number in 1..6 {
    if number == 3 {
        continue;  // Skips the number 3.
    }
    println!("{}", number);
  }
  ```

In conclusion, control flow constructs in Rust, like conditionals and loops, provide the flexibility to dictate how and when certain blocks of code are executed. By understanding and effectively using these constructs, developers can create more dynamic, efficient, and logical programs.

## Functions and Modules

In Rust, functions are the primary building blocks of your program. They allow you to bundle code into reusable and self-contained units. Modules, on the other hand, help in organizing these functions and other items, like structs and traits, into separate namespaces, facilitating better readability and maintainability. This chapter delves into the intricacies of functions and modules in Rust.

1. `Functions`:

- `Defining and Calling Functions`:
  Functions are declared using the `fn` keyword.

  ```rs
  fn greet() {
    println!("Hello, world!");
  }

  // Calling the function
  greet();
  ```

- `Function Parameters`:
  Functions can have parameters that allow you to pass values to them.

  ```rs
  fn add(x: i32, y: i32) {
    println!("The sum is: {}", x + y);
  }
  ```

- `Return Values`:
  Functions can return values using the `->` syntax.

  ```rs
  fn square(x: i32) -> i32 {
    x * x
  }
  ```

- `Expression-Based Language`:
  In Rust, the last expression in a function is automatically returned, unless ended with a semicolon.
  ```rs
  fn subtract(a: i32, b: i32) -> i32 {
    a - b  // No semicolon, so this value is returned
  }
  ```

2. `Modules`:

- `Defining Modules`:
  Modules are defined using the `mod` keyword.

  ```rs
  mod utilities {
    pub fn print_details() {
        println!("This is a utility function.");
    }
  }
  ```

- `Accessing Module Contents`:
  By default, functions in a module are private. To make them accessible from outside the module, use the `pub` keyword.

  ```rs
  utilities::print_details();
  ```

- `Nested Modules`:
  Modules can be nested within other modules.

  ```rs
  mod outer {
    pub mod inner {
        pub fn show() {
            println!("Inside the inner module.");
        }
    }
  }
  ```

- `Using the use Keyword`:
  The `use` keyword allows you to bring paths into scope, simplifying code.

  ```rs
  use outer::inner;

  inner::show();
  ```

- `The pub use Re-export`:
  This allows external code to use the re-exported item as if it's part of the module.

  ```rs
  mod outer {
    pub mod inner {
        pub fn show() {
            println!("Inside the inner module.");
        }
    }
    pub use inner::show;
  }

  outer::show();
  ```

- `Separating Modules into Different Files`:
  For larger projects, you can move module definitions to separate files.

  ```rs
  // In lib.rs or main.rs
  mod utilities;

  // In utilities.rs
  pub fn print_details() {
    println!("This is a utility function.");
  }
  ```

In conclusion, functions and modules are essential components of Rust programming. While functions encapsulate behavior, modules help in organizing and structuring your codebase, making it more modular and maintainable. By mastering these concepts, developers can write clean, efficient, and modular Rust programs.
