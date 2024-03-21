# Array Manipulation in JavaScript

## 1. arr.push(4);

push() method adds one or more elements to the end of an array and returns the new length of the array.

Example:

```javascript
let arr = [1, 2, 3];
arr.push(4); // Adds 4 to the end of the array
console.log(arr); // Output: [1, 2, 3, 4]
```

## 2. arr.pop();

pop() method removes the last element from an array and returns that element.

Example:

```javascript
let arr = [1, 2, 3, 4];
arr.pop(); // Removes 4 from the end of the array
console.log(arr); // Output: [1, 2, 3]
```

## 3. arr.shift();

shift() method removes the first element from an array and returns that removed element. It also shifts all other elements to a lower index.

Example:

```javascript
let arr = [1, 2, 3];
arr.shift(); // Removes 1 from the beginning of the array
console.log(arr); // Output: [2, 3]
```

## 4. arr.unshift(0);

unshift() method adds one or more elements to the beginning of an array and returns the new length of the array.

Example:

```javascript
let arr = [1, 2, 3];
arr.unshift(0); // Adds 0 to the beginning of the array
console.log(arr); // Output: [0, 1, 2, 3]
```

## 5. arr.slicing()

Use `slice()` to extract a portion of an array **without modifying** the original array.

Syntax:

```javascript
array.slice(startIndex, endIndex);
```

Example:

```javascript
let originalArray = [1, 2, 3, 4, 5];
let slicedArray = originalArray.slice(1, 4); // Extracts elements from index 1 to 3
console.log(slicedArray); // Output: [2, 3, 4]
console.log(originalArray); // Output: [1, 2, 3, 4, 5] (original array remains unchanged)
```

## 6. arr.filter()

This method create a new array with all elements that pass a certain condition provided by a callback function. This method doesn't modify the original array but instead returns a new array containing only the elements that meet the specified criteria.

Syntax:

```javascript

array.filter(callback(element[, index[, array]])[, thisArg])
```

- callback: A function to test each element of the array. It takes three arguments:
  - element: The current element being processed in the array.
  - index (Optional): The index of the current element being processed.
  - array (Optional): The array filter was called upon.
- thisArg (Optional): Value to use as this when executing the callback function.

Example:

```JavaScript
let numbers = [1, 2, 3, 4, 5];

// Filtering even numbers
let evenNumbers = numbers.filter(function(num) {
  return num % 2 === 0;
});

// OR

let evenNumbers = numbers.filter(num => num % 2 === 0);

console.log(evenNumbers); // Output: [2, 4]

```

## 7. arr.reduce()

The method in JavaScript is used to apply a function to each element in the array and reduce the array to a single value. It executes a provided function for each value of the array (from left to right), resulting in a single output value. This method is often used for tasks such as summing up values, calculating averages, or flattening arrays.

Syntax:

```javascript

array.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])
```

- callback: A function to execute on each element of the array. It takes four arguments:
  - accumulator: The accumulator accumulates the callback's return values. It is the accumulated result of previous executions.
  - currentValue: The current element being processed in the array.
  - index (Optional): The index of the current element being processed.
  - array (Optional): The array reduce was called upon.
- initialValue (Optional): A value to use as the first argument to the first call of the callback. If no initial value is supplied, the first element in the array will be used as the initial accumulator value and skipped as currentValue.

```javascript
let numbers = [1, 2, 3, 4, 5];

// Calculating the sum of all numbers using arrow function
let sum = numbers.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  0
);

console.log(sum); // Output: 15
```

## 8. `arr.map()`

The `map()` method creates a new array populated with the results of calling a provided function on **every element** in the calling array. It's often used to transform each element of the array in some way.

Syntax:

```javascript
let newArray = array.map(function callback(currentValue, index, array) {
  // Return element for newArray
}, thisArg);
```

Example:

```javascript
let numbers = [1, 2, 3, 4, 5];

// Doubling each number in the array
let doubledNumbers = numbers.map((num) => num * 2);

console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]
```

## 9. `arr.every()`

The every() method tests whether all elements in the array pass the test implemented by the provided function. It returns **true if all elements pass the test**, otherwise false.

Syntax:

```javascript
let result = array.every(function callback(currentValue, index, array) {
  // Return true or false based on condition
}, thisArg);
```

Example:

```javascript
let numbers = [1, 2, 3, 4, 5];

// Checking if all numbers are greater than 0
let allPositive = numbers.every((num) => num > 0);

console.log(allPositive); // Output: true
```

## 10. `arr.some()`

The some() method tests whether at least one element in the array passes the test implemented by the provided function. It returns **true if at least one element passes the test**, otherwise false.

Syntax:

```javascript
let result = array.some(function callback(currentValue, index, array) {
  // Return true or false based on condition
}, thisArg);
```

Example:

```javascript
let numbers = [1, 2, 3, 4, 5];

// Checking if there is at least one even number
let hasEvenNumber = numbers.some((num) => num % 2 === 0);

console.log(hasEvenNumber); // Output: true
```

## Summary

| Method      | Description                                                                                        | Example                            |
| ----------- | -------------------------------------------------------------------------------------------------- | ---------------------------------- |
| `push()`    | Adds element(s) to the end of the array                                                            | `arr.push(4);`                     |
| `pop()`     | Removes the last element from the array                                                            | `arr.pop();`                       |
| `shift()`   | Removes the first element from the array                                                           | `arr.shift();`                     |
| `unshift()` | Adds element(s) to the beginning of the array                                                      | `arr.unshift(0);`                  |
| `slice()`   | Extracts a portion of an array **without modifying** the original                                  | `arr.slice(startIndex, endIndex);` |
| `filter()`  | Creates a new array with elements passing a condition provided by a callback function              | `arr.filter(callback);`            |
| `reduce()`  | Applies a function to each element in the array and reduces the array to a single value            | `arr.reduce(callback);`            |
| `map()`     | Creates a new array with results of calling a function on every element in the calling array       | `arr.map(callback);`               |
| `every()`   | Tests whether all elements in the array pass a condition provided by a callback function           | `arr.every(callback);`             |
| `some()`    | Tests whether at least one element in the array passes a condition provided by a callback function | `arr.some(callback);`              |

> push() and pop() are used to add and remove elements from the **_end_** of an array, respectively.

> shift() and unshift() are used to remove and add elements to the **_beginning_** of an array, respectively.
