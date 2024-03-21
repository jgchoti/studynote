# Object and Object Manipulation in JavaScript

## Objects in JavaScript

- Objects in JavaScript are essential data structures that allow us to store collections of key-value pairs.

- They serve as blueprints for organizing and managing data efficiently within our code.

## Creating Objects

Objects are created using curly braces `{}` and consist of key-value pairs. Each key is a unique identifier associated with a value. For example:

```javascript
let person = {
  name: "Tom",
  age: 27,
  eyeColor: "blue",
  updateAge: function () {
    return ++this.age;
  },
};
```

## Accessing Object Properties

Properties of an object can be accessed

- using dot notation (object.property)
- bracket notation (object['property']).

Example:

```javascript
console.log(person.name); // Output: Tom
console.log(person["age"]); // Output: 27
```

## Manipulating Objects

### Adding Properties:

Properties can be added to an object by simply assigning a value to a new key.

```javascript
let person = {
  name: "John",
  age: 30,
};

// Adding a new property
person.city = "New York";
console.log(person); // Output: { name: 'John', age: 30, city: 'New York' }
```

### Removing Properties

Properties can be removed using the `delete` keyword.

```javascript
let person = {
  name: "John",
  age: 30,
  city: "New York",
};

// Removing a property
delete person.city;
console.log(person); // Output: { name: 'John', age: 30 }
```

### Object Methods

Objects can contain methods, which are functions stored as property values. These methods can perform operations on the object's data.

```javascript
let calculator = {
  number1: 0,
  number2: 0,

  // Method to add
  add: function () {
    return this.number1 + this.number2;
  },

  // Method to subtract
  subtract: function () {
    return this.number1 - this.number2;
  },
};

// Setting operands
calculator.number1 = 10;
calculator.number2 = 5;

console.log(calculator.add()); // Output: 15
console.log(calculator.subtract()); // Output: 5
```

---

## Object Constructors

- Object constructors allow us to create multiple instances of an object with similar properties and methods.
- We define a blueprint for the object, and then create instances based on that blueprint.

Example:

```javascript
function Person(name, age, eyeColor) {
  this.name = name;
  this.age = age;
  this.eyeColor = eyeColor;
  this.updateAge = function () {
    return ++this.age;
  };
}

let person1 = new Person("Tom", 27, "blue");
let person2 = new Person("Alice", 30, "green");
```

### Advantages of Object Constructors

- Using object constructors helps in organizing data and reducing redundancy.
- It allows for the creation of multiple instances of an object with ease, enabling efficient management of related data.

## Ref

[Javascript Objects Explained](https://www.youtube.com/watch?v=rLPwCAqyCAE)
[What Are Objects in JavaScript](https://www.youtube.com/watch?v=4uVwGw317QM)
[How to Create Object Constructors](https://www.youtube.com/watch?v=e1yBONtbTuA&t=2s)
