# Chapter 4

# Control Structures

Control structures are an essential aspect of programming that allows you to manage the flow of your code. By using conditional statements and loops, you can create more dynamic and efficient programs. This chapter will discuss various control structures in JavaScript, including conditional statements (`if/else`, `switch`), loops (`for`, `while`, `do-while`), and techniques for breaking and continuing loops.

## Conditional Statements (if/else, switch)

Conditional statements allow you to execute different blocks of code based on specific conditions. The most common conditional statements in JavaScript are `if/else` and `switch`.

### If/else

`if/else` statements are used to execute a block of code if a certain condition is true, and another block of code if the condition is false.

```javascript
let age = 25;

if (age >= 18) {
  console.log("You are an adult");
} else {
  console.log("You are a minor");
}
```

### Switch

A `switch` statement is used to select and execute a block of code from multiple options based on the value of an expression.

```javascript
let day = 3;
let dayName;

switch (day) {
  case 1:
    dayName = "Monday";
    break;
  case 2:
    dayName = "Tuesday";
    break;
  case 3:
    dayName = "Wednesday";
    break;
  case 4:
    dayName = "Thursday";
    break;
  case 5:
    dayName = "Friday";
    break;
  case 6:
    dayName = "Saturday";
    break;
  case 7:
    dayName = "Sunday";
    break;
  default:
    dayName = "Invalid day number";
}

console.log(dayName); // Output: Wednesday
```

## Loops (for, while, do-while)

Loops are used to execute a block of code repeatedly until a specific condition is met. The three main types of loops in JavaScript are `for`, `while`, and `do-while`.

### For Loop

A `for` loop is used when you know the number of times you want to execute a block of code.

```javascript
for (let i = 0; i < 5; i++) {
  console.log(`Iteration ${i}`);
}
```

### While Loop

A `while` loop is used when you want to execute a block of code as long as a specific condition is true.

```javascript
let counter = 0;

while (counter < 5) {
  console.log(`Iteration ${counter}`);
  counter++;
}
```

### Do-while Loop

A `do-while` loop is similar to a `while` loop but guarantees that the block of code will be executed at least once, even if the condition is false from the beginning.

```javascript
let counter = 0;

do {
  console.log(`Iteration ${counter}`);
  counter++;
} while (counter < 5);
```

## Breaking and Continuing Loops

Sometimes, you may want to exit a loop early or skip an iteration. You can use the `break` and `continue` statements to achieve this.

### Break

The `break` statement is used to exit a loop early.

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break;
  }
  console.log(`Iteration ${i}`);
}
```

### Continue

The `continue` statement is used to skip an iteration in a loop.

```javascript
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) {
    continue;
  }
  console.log(Iteration ${i});
}
```

In this example, the `continue` statement is used to skip even numbers in the loop, so only odd numbers will be printed to the console.

## Best Practices for Loop Performance

When writing loops, consider these best practices to improve performance:

1. Cache the length of an array when using a `for` loop.

```javascript
let arr = [1, 2, 3, 4, 5];
let arrLength = arr.length;

for (let i = 0; i < arrLength; i++) {
  console.log(arr[i]);
}
```

By caching the length of the array, you avoid recalculating it on each iteration, improving performance.

2. Use for...of and for...in loops for simpler code when appropriate.

```javascript
let arr = [1, 2, 3, 4, 5];

for (const value of arr) {
  console.log(value);
}
```

The `for...of` loop is more concise and less error-prone than a traditional `for` loop.

In conclusion, control structures like conditional statements and loops are fundamental components of JavaScript programming. By understanding how to use `if/else`, `switch`, `for`, `while`, and `do-while` statements, you can create dynamic and efficient code. Additionally, leveraging the `break` and `continue` statements allows you to have more control over the flow of your loops. Following best practices for loop performance will ensure that your code is both effective and performant.

## Summing up

In Chapter 4, we explored control structures in JavaScript, which are essential for managing the flow of your code. We discussed conditional statements such as if/else and switch, which enable different blocks of code to be executed based on specific conditions. We also examined loops, including for, while, and do-while, which allow you to run a block of code repeatedly until a certain condition is met. We delved into techniques for breaking and continuing loops using the break and continue statements for better control over the flow. Lastly, we reviewed best practices for loop performance, such as caching the length of an array and using for...of and for...in loops when appropriate. By understanding these control structures, you can create dynamic and efficient JavaScript code.

## Knowledge Test

1. Write a JavaScript program that takes a user's age as input and prints whether the user can legally vote or not. If the user is 18 years or older, print "You can vote!", otherwise print "You cannot vote yet."?

2. Write a JavaScript program that takes a number between 1 and 7 as input, representing the day of the week, and prints the corresponding day name. If the input is invalid, print "Invalid input."?

3. Write a JavaScript program that prints the multiplication table of a given number up to 10 using a `for` loop. For example, if the input is 5, the program should print the following:

```bash
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
...
5 x 10 = 50
```

4. Write a JavaScript program that prints all the prime numbers between 2 and a given number using a `while` loop?

5. Write a JavaScript program that prompts the user for a secret password. The program should keep asking the user for the password until the correct password is entered, using a `do-while` loop. When the correct password is entered, print "Access granted."?

6. Write a JavaScript program that uses a `for` loop to iterate over the numbers from 1 to 100. The program should print the square of each number, but if the square is divisible by 10, it should skip that iteration using the `continue` statement. If the square is greater than 2000, the program should exit the loop using the `break` statement.

7. Given an array of numbers, write a JavaScript program that calculates the sum of all the elements in the array using a `for` loop. Optimize the loop performance by caching the length of the array.
