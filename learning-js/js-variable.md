# Variable Definition

- A variable is like a box in programming.
- It has a unique name that helps describe its contents.
- The name that assign to a variable should be easy to remember
and understand the purpose of the variable.

## Variable Creation in JavaScript

- In JavaScript, there are three ways to declare variables: `var`, `let`, and `const`.
- `var` was traditionally used,
but `let` and `const` offer more predictable scoping behavior.

## Declaration with `var`, `let`, and `const`

- `var`: Declares a variable
globally or locally to a function, and it can be reassigned.
- `let`: Introduces block-scoping, allowing a variable to be limited to the block,
statement, or expression where it is defined. **It can be reassigned.**
- `const`: Also block-scoped, but it cannot be reassigned after initialization.
It is typically used for values that **should not be changed.**

## Assignment Operation

- The equal sign (`=`) is used as an assignment operator.
- It indicates that whatever is on the right side of the equal sign will be
stored in the variable on the left side.

## Storing Data

- Variables can store various types of data.
- In the provided example, a string of characters (a string) is stored in the variable.

## Primary Data Types in JavaScript

| #    | Data Type   | |
| ---- | ----------- | ----------------------------------------------------- |
| 1    | Undefined   | Default value when a variable is declared but not assigned. |
| 2    | Null        | Represents the intentional absence of any object value. |
| 3    | Boolean     | Represents logical values `true` or `false`.           |
| 4    | Number      | Represents numeric values, including both integers and floating-point numbers. |
| 5    | BigInt      | Represents whole numbers of any size, allowing for precise handling of very large integers |
| 6    | String      | Represents textual data, enclosed in single or double quotes. |
| 7    | Symbol      | Represents unique and immutable values to create completely unique identifiers|
| 8    | Object      | Represents a collection of key-value pairs.            |

#### Difference between undefined and null

|                  | Undefined                                                | Null                               |
|------------------|----------------------------------------------------------|------------------------------------|
| **Definition**   | A variable has been declared but has not yet been assigned a value. | An assignment value representing no value. |
| **Origin**       | An ECMAScript (ES1) feature.                               | A primitive value in JavaScript.   |
| **Syntax**       | Does not have any specific syntax. It can be assigned to a variable, but it is not typically done intentionally. | `null`                             |
| **Type**         | Not a global property.                                    | A global property.                  |
| **Assignment**   | Can be unintentionally assigned by declaring a variable without assigning a value. | Explicitly assigned to a variable to represent the absence of value. |

[Undefined Vs Null in JavaScript](https://www.geeksforgeeks.org/undefined-vs-null-in-javascript/)

#### Boolean Values in JavaScript

In JavaScript, the following values evaluate to false in a boolean context:
- false
- null
- undefined
- 0
- -0
- NaN
- An empty string ('')

## Example Scenario

| #    | Data Type   | Example                                          |
| ---- | ----------- | ------------------------------------------------- |
| 1    | Undefined   | `let myVariable;`                                |
| 2    | Null        | `let myVariable = null;`                         |
| 3    | Boolean     | `let isTrue = true;`                             |
| 4    | Number      | `let myNumber = 42;`                             |
| 5    | BigInt      | `let bigInteger = 1234567890123456789012345678901234567890n;` |
| 6    | String      | `let myString = "Hello, World!";`               |
| 7    | Symbol      | `const uniqueSymbol = Symbol('uniqueKey');`     |
| 8    | Object      | `let myObject = { key: 'value' };`              |

## Conclusion

- Variables, declared with `var`, `let`, or `const`, allow programmers to store and manage data effectively in a program.
- They act as containers with unique names, making it easier to work with and understand the code.
