# Copying Arrays and Objects in JavaScript

## 1. Shallow Copy For Objects

Shallow copy refers to the process of creating a new object or array and copying the top-level structure of the original object or array.

### 1.1 Object.assign() for Shallow Copy:

The `Object.assign()` method in JavaScript is frequently used to duplicate objects. It generates a shallow copy of an object by replicating its properties into a new object.

```javascript
let person = { name: "Max", hobbies: ["sports", "cooking"] };
let secondPerson = Object.assign({}, person);
person.name = "Chris";
person.hobbies.push("reading");
console.log(secondPerson); // Output: { name: "Max", hobbies: ["sports", "cooking", "reading"] }
```

> `Object.assign()` performs a shallow copy, meaning it copies only the top-level properties of an object. However, for nested objects or arrays, it copies the reference, not the actual values.
> As a result, changes made to nested properties in the original object are reflected in the cloned object as well.Object.assign() performs a shallow copy, replicating only the top-level properties of an object. Nested properties are copied by reference, reflecting changes made to them in the original object.

### 1.2 Object.create() for Shallow Copy:

Another method for creating shallow copies of objects is Object.create(). It creates a new object with the specified prototype object and properties.

```javascript
let person = { name: "Max", hobbies: ["sports", "cooking"] };
let secondPerson = Object.create(
  Object.getPrototypeOf(person),
  Object.getOwnPropertyDescriptors(person)
);

// Making modifications to the original object
person.name = "Chris";
person.hobbies.push("reading");

console.log(secondPerson);
// Output: { name: "Max", hobbies: ["sports", "cooking", "reading"] }
```

> Similar to Object.assign(), Object.create() performs a shallow copy, meaning it copies the top-level properties of the object. Changes to nested properties in the original object will still affect the cloned object.

### 1.3 Spread Operator for Shallow Copy

The spread operator, introduced in ES6, can spread values into an object using three dots ({ ... }). It creates a shallow copy of an object by copying its properties. Unlike Object.assign() and Object.create(), which are methods, the spread operator provides a concise and elegant syntax for object copying.

```js
// Declaring Object
const userDetails = {
  name: "John Doe",
  age: 14,
  verified: false,
};

// Cloning the Object with Spread Operator
let cloneUser = { ...userDetails };

console.log(cloneUser); // {name: 'John Doe', age: 14, verified: false}
```

## 2. Deep Clone For Objects

### 2.1 Using JSON.stringify() for Deep Cloning

- **Advantages**:
  - Simple and easy to use.
    Works well for simple data structures.
- **Limitations**:
  - Cannot handle circular references (objects referencing themselves).
  - Does not preserve functions or undefined values.

```javascript
const obj = { name: "John", age: 30 };
const clonedObj = JSON.parse(JSON.stringify(obj));
```

> JSON.parse() is a built-in JavaScript method used to parse JSON (JavaScript Object Notation) strings and convert them into JavaScript objects.

### 2.2 Using structuredClone() for Deep Cloning

- **Advantages:**
  - Handles circular references gracefully.
  - Preserves functions and a wider range of data types.
- **Limitations:**
  - Availability may vary across browsers.

```javascript
const obj = { name: "John", age: 30 };
const clonedObj = structuredClone(obj);
```

> When dealing with complex objects or circular references, structuredClone() is the preferred choice as it provides more reliable deep cloning functionality.

---

## 3. Copy For Array

Both array.slice() and Array.from(array) create shallow copies of arrays. They copy the elements of the original array into a new array, ensuring that modifications made to the original array do not affect the copied one. However, they do not handle nested arrays, copying them by reference.

**To copy Array**

- `array.slice()`
- `Array.from(array)`

```javascript
let hobbies = ["sports", "cooking"];
let myHobbies1 = hobbies; // Incorrect way - creates a reference, not a copy
let myHobbies2 = hobbies.slice(); // Correct way - creates a real copy
let myHobbies3 = Array.from(hobbies); // Another correct way - creates a real copy
hobbies.push("reading");
console.log(myHobbies2); // Output: ["sports", "cooking"]
```

> Even though we modified the hobbies array by adding "reading," the `myHobbies2` array remains unaffected. This behavior ensures that both arrays are distinct entities with their own set of values.

---

## Summary

| Method                         | Advantages                                      | Limitations                                            |
|--------------------------------|-------------------------------------------------|---------------------------------------------------------|
| Object.assign()                | Simple usage, shallow copy                      | Copies nested properties by reference                   |
| Object.create()                | Prototype-based, shallow copy                   | Copies nested properties by reference                   |
| JSON.stringify()               | Simple, handles basic data structures          | Fails with circular references, lacks function support  |
| structuredClone()              | Handles circular references, preserves functions| Browser compatibility may vary, more complex usage      |
| array.slice()                  | Simple usage, creates true copy of array       | Limited to arrays, does not handle nested arrays        |
| Array.from(array)              | Simple usage, creates true copy of array       | Limited to arrays, does not handle nested arrays        |
| Spread Method ({ ...obj })     | Simple usage, creates true copy of object      | Limited to object cloning, does not handle nested objects |



#### List of References

- [modern way to deep clone object in javascript](https://medium.com/@saikiran-dev/absolute-modern-way-to-deep-clone-object-in-javascript-61f0282db8de)

- [clone object in javascript](https://www.freecodecamp.org/news/clone-an-object-in-javascript/)
