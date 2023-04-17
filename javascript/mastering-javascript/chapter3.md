# Chapter 3

# Operators and Expressions

In this chapter, we will examine the essential components of JavaScript programming: operators and expressions. Operators allow you to perform various operations on values, while expressions combine these operations to create more complex functionality. Understanding these concepts is crucial for writing effective and efficient code.

## Arithmetic Operators

JavaScript provides arithmetic operators for performing basic mathematical operations like addition, subtraction, multiplication, division, and modulo (remainder).

```javascript
let a = 10;
let b = 5;

let sum = a + b; // 15
let difference = a - b; // 5
let product = a * b; // 50
let quotient = a / b; // 2
let remainder = a % b; // 0
```

## Comparison Operators

Comparison operators are used to compare two values and return a boolean value, either true or false. The primary comparison operators in JavaScript are:

```javascript
let x = 10;
let y = 5;

let isEqual = x == y; // false
let isNotEqual = x != y; // true
let isGreater = x > y; // true
let isLess = x < y; // false
let isGreaterOrEqual = x >= y; // true
let isLessOrEqual = x <= y; // false
```

## Logical Operators

Logical operators are used to combine multiple conditions or expressions and return a boolean value. The primary logical operators in JavaScript are:

```javascript
let a = true;
let b = false;

let andOperator = a && b; // false
let orOperator = a || b; // true
let notOperator = !a; // false
```

## Conditional (Ternary) Operator

The conditional (ternary) operator is a shorthand way of writing an if-else statement. It takes three operands: a condition, the value to return if the condition is true, and the value to return if the condition is false.

```javascript
let a = 10;
let b = 5;

let max = a > b ? a : b; // 10
```

## Assignment Operators

Assignment operators are used to assign values to variables. In addition to the basic assignment operator (=), JavaScript also provides compound assignment operators that perform an operation and assignment in a single step.

```javascript
let x = 10;

x += 5; // x = x + 5, x is now 15
x -= 3; // x = x - 3, x is now 12
x *= 2; // x = x * 2, x is now 24
x /= 4; // x = x / 4, x is now 6
x %= 5; // x = x % 5, x is now 1
```

## Operator Precedence

Operator precedence determines the order in which operators are evaluated in an expression. Higher precedence operators are evaluated before lower precedence operators. Parentheses can be used to change the order of evaluation.

```javascript
let result = 10 + 5 * 2; // 20, multiplication has higher precedence than addition
let parenthesesResult = (10 + 5) * 2; // 30, parentheses change the order of evaluation
```

## Expressions and Statements

Expressions are combinations of values, variables, and operators that produce a single value. Statements, on the other hand, are lines of code that perform an action, such as declaring a variable or calling a function. Expressions can be used as part of statements.

```javascript
let expression = 10 * (5 + 2); // 70
let statement = console.log(expression); // Output: 70
```

In the example above, the expression `10 \* (5 + 2)` is evaluated to produce the value `70`, which is then assigned to the variable `expression`. The statement `console.log(expression)` is an action that logs the value of `expression` to the console.

Understanding the difference between expressions and statements is crucial for writing clear and concise code. Expressions produce a value and can be combined with other expressions to create more complex functionality, while statements perform an action and control the flow of the program.

In conclusion, operators and expressions form the core building blocks of JavaScript programming. By understanding how to use arithmetic, comparison, logical, conditional, and assignment operators, you can create powerful and efficient code. Additionally, recognizing the difference between expressions and statements is essential for writing clear and concise code. Combining these concepts allows you to create more complex functionality and control the flow of your programs effectively.

## Summing up

In Chapter 3, we delved into the essential components of JavaScript programming: operators and expressions. Operators, including arithmetic, comparison, logical, conditional, and assignment operators, facilitate various operations on values, while expressions combine these operations to yield more complex functionality. By grasping these concepts, programmers can create powerful and efficient code. Furthermore, differentiating between expressions, which generate a value, and statements, which perform actions and govern the program's flow, is crucial for writing clear and concise code. In sum, understanding operators and expressions and applying these concepts enable developers to produce intricate functionality and effectively manage their program's flow.

## Knowledge Test

- Create two variables `num1` and `num2`, and assign them values of 25 and 12, respectively. Perform the following operations and log the results to the console:

a. Add `num1` and `num2`
b. Subtract `num2` from `num1`
c. Multiply `num1` and `num2`
d. Divide `num1` by `num2`
e. Find the remainder when `num1` is divided by `num2`

- Compare the values of num1 and num2 using comparison operators, and log the results to the console:

a. Check if `num1` is equal to `num2`
b. Check if `num1` is not equal to `num2`
c. Check if `num1` is greater than `num2`
d. Check if `num1` is less than `num2`
e. Check if `num1` is greater than or equal to `num2`
f. Check if `num1` is less than or equal to `num2`

- Use logical operators to evaluate and log the following expressions:

a. `num1` is greater than 20 AND `num2` is less than 15
b. `num1` is less than 30 OR `num2` is greater than 10
c. NOT (`num1` is equal to 25)

- Use the conditional (ternary) operator to assign the minimum value of `num1` and `num2` to a variable called `minValue`, and log the result to the console.

- Update the value of `num1` using compound assignment operators:

a. Increment `num1` by 5
b. Decrement `num1` by 3
c. Multiply `num1` by 4
d. Divide `num1` by 2
e. Get the remainder when `num1` is divided by 7

- Calculate and log the result of the following expression, taking operator precedence into account: (`num1` + `num2`) \* (`num1` - `num2`) / `num2` + 5.

- Write an expression that calculates the square of `num1`, and log the result to the console.
