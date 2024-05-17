# Asynchronous Programming

## Overview

JavaScript operates on a single-threaded, synchronous execution model, which means it processes one line of code at a time from top to bottom. However, modern web development requires handling tasks that may take an indeterminate amount of time, such as network requests or reading files. This is where asynchronous programming comes into play.

Let's take a basic example:

```javascript
let pizza;
console.log(pizza);
```

> This is synchronous code, because it goes step by step.
> Even though it’s very fast, it still takes a little time for each line to execute before going to the next one.

```javascript
function makePizza() {
  return "🍕";
}

let pizza = makePizza();
console.log(pizza);
```

This function is **synchronous.**
Synchronous means things happen together
in the order they were set up, in a synchronized way.

## Visualizing Synchronous vs Asynchronous Code

![Synchronous vs Asynchronous](https://www.freecodecamp.org/news/content/images/size/w2000/2021/09/freeCodeCamp-Cover-2.png)

### Why Asynchronous?

When you order a pizza in real life, you don't just sit around waiting. You might call a friend, do some laundry, watch TV, or write some code until the pizza shows up. Similarly, you want some parts of your code to continue running no matter how long other parts take.

## JavaScript Runtime Components

### Event Loop:

The event loop is responsible for checking the call stack and the callback queue. If the stack is empty, it moves the first callback from the queue to the stack, thus executing it.

#### Key Steps in the Event Loop

1. **Evaluate Script:** Synchronously execute the script as though it were a function body. Run until the Call Stack is empty.
2. **Run a Task:** Select the oldest Task from the Task Queue. Run it until the Call Stack is empty.
3. **Run all Microtasks:** Select the oldest Microtask from the Microtask Queue. Run it until the Call Stack is empty. Repeat until the Microtask Queue is empty.

4. **Rerender the UI:** Rerender the UI if needed. This step only applies to browsers, not NodeJS. Then, return to step 2.

### Call Stack:

The call stack is a data structure that tracks function calls in a program. When a function is called, it's added to the stack (pushed). When a function returns, it's removed from the stack (popped).

> So, just like the pizza orders are processed in the order they were placed, JavaScript executes function calls in the order they were made. This ensures that things happen in a neat and orderly manner, without any confusion about which function should be dealt with next.

### Task Queue and Microtask Queue:

These queues hold tasks and microtasks, respectively, that are waiting to be executed. Both are managed by the Event Loop, which periodically checks them and moves tasks to the Call Stack for execution when it's ready. Tasks can include things like timers (setTimeout), DOM events, or AJAX requests, while microtasks are typically related to promises and other asynchronous operations.

### Web APIs:

These are extra features provided by the browser (or environment like Node.js). They handle asynchronous tasks like setTimeout, AJAX requests, and DOM manipulation. These APIs are not part of the JavaScript runtime itself.

#### Example with setTimeout

```javascript
let pizza;

function orderPizza() {
  setTimeout(() => {
    pizza = "🍕";
    console.log("Pizza is ready:", pizza);
  }, 2000);
}

console.log("Ordering pizza...");
orderPizza();
console.log("Pizza was ordered");
console.log("Eating pizza:", pizza);
```

In this example, `setTimeout` is an asynchronous function.
It means it’s not synchronized with the rest of the code. When we run it, the console logs "Ordering pizza...",
then it immediately logs "Pizza was ordered", and "Eating pizza: undefined". Finally, after two seconds, "Pizza is ready: 🍕" is logged.

### Callback Queue

> This queue holds callbacks that are waiting to be executed once the stack is clear.

This queue is also managed by the Event Loop and holds callback functions that are waiting to be executed. However, callback functions in the Callback Queue typically result from asynchronous operations like setTimeout, AJAX requests, or event handlers. When these operations complete, their associated callback functions are placed in the Callback Queue. The Event Loop then moves these callback functions to the Call Stack for execution when the stack is empty and the program is ready to handle them.

> the Task Queue and Microtask Queue are more general-purpose, while the Callback Queue specifically deals with callback functions resulting from asynchronous operations.

#### Using Callbacks

One way to handle this is by using callbacks. Here’s an example:

```javascript
function orderPizza(callback) {
  setTimeout(() => {
    const pizza = "🍕";
    callback(pizza);
  }, 2000);
}

function eatPizza(pizza) {
  console.log("Eating pizza:", pizza);
}

orderPizza(eatPizza);
console.log("Calling friend...");
```

In this setup, `orderPizza` takes a callback function. It calls the callback with the pizza once it’s ready.

#### Callback Hell

The problem with callbacks is they can become difficult to read if you have many dependent tasks. This is known as callback hell:

```javascript
function callShop(callback) {
  setTimeout(() => {
    console.log("Called shop");
    callback();
  }, 1000);
}

function orderPizza(callback) {
  setTimeout(() => {
    console.log("Ordered pizza");
    callback();
  }, 2000);
}

function eatPizza() {
  setTimeout(() => {
    console.log("Eating pizza");
  }, 3000);
}

callShop(() => {
  orderPizza(() => {
    eatPizza();
  });
});
```

> This code is hard to read and maintain.

### Summary

To recap:

- **Synchronous code** runs one line at a time, each line waiting for the previous one.
- **Asynchronous code** allows some operations to run independently of the main code flow.
- Key components of the JavaScript runtime include the call stack, heap, web APIs, event loop, and callback queue.
- Callbacks are functions passed to other functions to be executed later, enabling asynchronous behavior.
- Callback hell can make code difficult to read and maintain, leading to the need for better asynchronous handling techniques like Promises and async/await.
