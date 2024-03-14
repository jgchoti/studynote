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

## Summary

| Method      | Description                                   | Example           |
| ----------- | --------------------------------------------- | ----------------- |
| `push()`    | Adds element(s) to the end of the array       | `arr.push(4);`    |
| `pop()`     | Removes the last element from the array       | `arr.pop();`      |
| `shift()`   | Removes the first element from the array      | `arr.shift();`    |
| `unshift()` | Adds element(s) to the beginning of the array | `arr.unshift(0);` |

> push() and pop() are used to add and remove elements from the **_end_** of an array, respectively.

> shift() and unshift() are used to remove and add elements to the **_beginning_** of an array, respectively.
