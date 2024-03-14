# **Primitive Types & Reference Types**

## Study Note for Beginners

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

### 4. Copying Behavior:

- **Primitive Types (Copied by Value):** Actual value is copied.
- **Reference Types (Copied by Reference):** Memory address is copied.

### 5. Object.assign(), Object.create(), and Object Cloning

#### 5.1 Object.assign() for Shallow Copy:

The Object.assign() method in JavaScript is commonly used to clone **objects**. It creates a shallow copy of an object, meaning it copies the object's properties into a new object.

```javascript
let person = { name: "Max", hobbies: ["sports", "cooking"] };
let secondPerson = Object.assign({}, person);
person.name = "Chris";
person.hobbies.push("reading");
console.log(secondPerson); // Output: { name: "Max", hobbies: ["sports", "cooking", "reading"] }
```

> `Object.assign()` performs a shallow copy, meaning it copies only the top-level properties of an object. However, for nested objects or arrays, it copies the reference, not the actual values.
> As a result, changes made to nested properties in the original object are reflected in the cloned object as well.

#### 5.2 Object.create() for Shallow Copy:

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

### 6. Deep Clone For Objects

[ref](https://medium.com/@saikiran-dev/absolute-modern-way-to-deep-clone-object-in-javascript-61f0282db8de)

#### 6.1 Using JSON.stringify() for Deep Cloning

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

#### 6.2 Using structuredClone() for Deep Cloning

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

### 7. Deep Copy For Array

it's essential to understand the distinction between copying by reference and creating a true duplicate. The slice method provides a convenient way to achieve a genuine copy of an **array**.

```javascript
let hobbies = ["sports", "cooking"];
let myHobbies1 = hobbies; // Incorrect way - creates a reference, not a copy
let myHobbies2 = hobbies.slice(); // Correct way - creates a real copy
hobbies.push("reading");
console.log(myHobbies2); // Output: ["sports", "cooking"]
```

> Even though we modified the hobbies array by adding "reading," the `myHobbies2` array remains unaffected. This behavior ensures that both arrays are distinct entities with their own set of values.

### 8. Conclusion:

Understanding primitive and reference types, and their memory management, is crucial in JavaScript. Primitives are copied by value, while reference types are copied by reference, impacting how modifications affect variables.

### 9. Takeaways:

- **By Value vs. By Reference:** Mastering the distinction between these two concepts is fundamental to writing reliable JavaScript code.

- **Memory Management:** Primitives reside in the stack, while reference types (objects, arrays) live in the heap. Understand how memory is managed to avoid unexpected behavior.