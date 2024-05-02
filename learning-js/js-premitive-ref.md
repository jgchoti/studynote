# **Primitive Types & Reference Types**

### 1. Introduction to JavaScript Types:

JavaScript, a dynamically-typed language, categorizes its data into two main types: **Primitive Types** and **Reference Types**.

### 2. Primitive Types:

**Primitive types** include strings, booleans, numbers, undefined, null, and symbols. They are stored on the stack and are passed by value.

**Example (Primitive Type):**

```javascript
let a = 10;
let b = a;
a = 20;
console.log(a); // Output: 20
console.log(b); // Output: 10
```

### 3. Reference Types

**Reference types** involve objects, arrays, and functions. They are stored on the heap and are passed by reference.

**Example (Reference Type):**

```javascript
let objA = { value: 10 };
let objB = objA;
objA.value = 20;
console.log(objA.value); // Output: 20
console.log(objB.value); // Output: 20
```

When copying arrays, it's crucial to note that simply assigning one array variable to another doesn't create a new value but rather points both variables to the same array in memory.

```javascript
let array1 = [];
let array2 = array1;
```

In this example, array1 and array2 both reference the same array, so modifications to one will affect the other. To compare the values of two arrays, you'll need to iterate through them and compare each value individually.

![Primitive Types & Reference Types](https://miro.medium.com/v2/resize:fit:1400/1*z1Cacf_OSbsQ1rYYaQsXYA.png)

---

### 4. Copying Behavior:

- **Primitive Types (Copied by Value):** Actual value is copied.
- **Reference Types (Copied by Reference):** Memory address is copied.

[Ref](https://www.geeksforgeeks.org/primitive-and-reference-value-in-javascript/)

![Copied by Reference](https://media.geeksforgeeks.org/wp-content/uploads/20201227083737/gfgfgfgfgffg-660x415.png)

---

### 5. Side Effects in Functions

Arrays can be modified inside functions, affecting their values outside the function scope. This is known as a side effect.

To prevent unintended side effects, **\*it's recommended to create a new array inside the function rather than modifying the original array:**

```javascript
function modifyArray(array) {
  // Create a new array to avoid modifying the original array
  let newArray = array.slice();
  // Perform modifications on the new array
  newArray.push("new value");
  return newArray;
}

let originalArray = ["old value"];
let modifiedArray = modifyArray(originalArray);
console.log(originalArray); // Output: ["old value"]
console.log(modifiedArray); // Output: ["old value", "new value"]
```

> By creating a new array (newArray)
> within the function and performing modifications on it, the original array (originalArray) remains unchanged outside the function.

This approach helps maintain the integrity of data and prevents unexpected behavior caused by side effects.

---

### 6. Conclusion:

Understanding primitive and reference types, and their memory management, is crucial in JavaScript. Primitives are copied by value, while reference types are copied by reference, impacting how modifications affect variables.

### 7. Takeaways:

- **By Value vs. By Reference:** Mastering the distinction between these two concepts is fundamental to writing reliable JavaScript code.

- **Memory Management:** Primitives reside in the stack, while reference types (objects, arrays) live in the heap. Understand how memory is managed to avoid unexpected behavior.

- **Garbage Collection**:
  JavaScript's garbage collection mechanism automatically removes values that are no longer referenced, freeing up memory.

- [Copying Arrays and Objects in JavaScript]
