# Chapter 5

# Functions

Functions are reusable blocks of code that can be defined and called by name. They can take input parameters and return output values. Functions allow you to break your code into smaller, modular pieces, making it easier to understand, maintain, and test. This chapter will cover defining and calling functions, function arguments and parameters, returning values, function expressions and arrow functions, function scope and closures, higher-order functions, and best practices for writing functions.

## Defining and Calling Functions

To define a function in JavaScript, you use the `function` keyword followed by the function name, a list of parameters, and the function body enclosed in curly braces.

```javascript
function greet(name) {
  console.log(`Hello, ${name}!`);
}

// To call the function, use its name followed by the arguments in parentheses:
greet("Alice");
```

## Function Arguments and Parameters

Functions can take any number of input values, called arguments. When defining a function, you list the expected input values as parameters.

```javascript
function add(a, b) {
  return a + b;
}

console.log(add(3, 4)); // Output: 7
```

## Returning Values from Functions

Functions can return a value using the `return` keyword. If a function doesn't have a `return` statement, it returns `undefined`.

```javascript
function multiply(a, b) {
  return a * b;
}

let result = multiply(3, 4);
console.log(result); // Output: 12
```

## Function Expressions and Arrow Functions

Functions can also be defined as expressions by assigning an anonymous function to a variable.

```javascript
const square = function (number) {
  return number * number;
};

console.log(square(5)); // Output: 25
```

Arrow functions are a shorter syntax for writing function expressions.

```javascript
const square = (number) => {
  return number * number;
};

// Or, for single-line functions with a single argument, you can omit the parentheses and curly braces:

const square = (number) => number * number;

console.log(square(5)); // Output: 25
```

## Function Scope and Closures

Variables declared inside a function are local to that function and have a function scope. They are not accessible outside the function.

```javascript
function showMessage() {
  let message = "Hello, world!";
  console.log(message);
}

showMessage(); // Output: Hello, world!
console.log(message); // Error: message is not defined
```

A closure is a function that has access to its outer function's variables, even after the outer function has returned.

```javascript
function outer() {
  let count = 0;

  function inner() {
    count++;
    console.log(count);
  }

  return inner;
}

const counter = outer();
counter(); // Output: 1
counter(); // Output: 2
```

## Higher-Order Functions

Higher-order functions are functions that take other functions as arguments or return functions as their result.

```javascript
function map(arr, func) {
  let result = [];

  for (let value of arr) {
    result.push(func(value));
  }

  return result;
}

const numbers = [1, 2, 3, 4, 5];
const doubled = map(numbers, (number) => number * 2);

console.log(doubled); // Output: [2, 4, 6, 8, 10]
```

## Best Practices for Writing Functions

1. Write small, focused functions that do one thing well.
2. Give functions clear and descriptive names.
3. Limit the number of function parameters to a reasonable amount (3 is often considered a good maximum).
4. Write comments to explain complex or non-obvious functionality.
5. Use default parameters to simplify function calls and improve readability.

```javascript
function greet(name, greeting = "Hello") {
  console.log(`${greeting}, ${name}!`);
}

greet("Alice"); // Output: Hello, Alice!
greet("Alice", "Hi"); // Output: Hi, Alice!
```

6. Use destructuring in function parameters to make it clear what properties the function expects from an object.

```javascript
function displayPerson({ firstName, lastName, age }) {
  console.log(`Name: ${firstName} ${lastName}, Age: ${age}`);
}

const person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
};

displayPerson(person); // Output: Name: John Doe, Age: 30
```

In summary, functions are a vital part of JavaScript programming, as they enable you to create reusable, modular code. By defining and calling functions, using arguments and parameters, returning values, and leveraging function expressions and arrow functions, you can write clean, maintainable code. Understanding function scope and closures is essential for working with more advanced topics like higher-order functions. Following best practices for writing functions ensures that your code is readable, efficient, and robust.

## Summing up

In Chapter 5, we explored functions, an essential aspect of JavaScript programming that allows you to create reusable, modular code. Functions help break down complex code into smaller, manageable pieces, which improves readability, maintainability, and testability. The chapter covered key concepts such as defining and calling functions, working with function arguments and parameters, returning values, utilizing function expressions and arrow functions, understanding function scope and closures, implementing higher-order functions, and adhering to best practices for writing functions. By mastering these concepts, you will be able to write clean, efficient, and robust code that effectively utilizes functions.

## Knowledge Test

- Write a function named `factorial` that takes a number as an argument and returns the factorial of the number?

- Write a function named `sum` that takes an array of numbers and returns the sum of all the numbers in the array?

- Write a function named `max` that takes two numbers and returns the greater of the two?

- Convert the `max` function from exercise 3 to an arrow function?

- Write a function named `filterEvens` that takes an array of numbers and returns a new array containing only the even numbers?

- Write a function named `makeGreeting` that takes two arguments, a greeting and a name, and returns a string with the greeting and the name. If the greeting is not provided, use a default greeting of "Hello"?

- Create a function named `lengths` that takes an array of strings and returns a new array containing the length of each string?

- Write a function named `findMax` that takes an array of numbers and returns the maximum value in the array using a higher-order function?
