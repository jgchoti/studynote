# Event Listeners

## What is an Event Listener?

An event listener is a function that waits for a specific event to occur
and then executes code in response to that event. Events can be triggered
by user interactions (like clicks or key presses) or by the browser itself
(like the page loading or an element being scrolled).

## Adding an Event Listener

To add an event listener to an element in JavaScript, you typically use the `addEventListener` method.
Here's the basic syntax:

```javascript
element.addEventListener(eventType, eventHandler);
```

> **element:** The DOM element you want to listen for events on.
> **eventType:** The type of event you want to listen for (e.g., 'click', 'keydown', 'submit', etc.)
> **eventHandler:** The function that will be called when the event occurs.

Example:

```javascript
const button = document.getElementById("myButton");

button.addEventListener("click", function (event) {
  console.log("Button clicked!");
});
```

### Types of Events

There are many types of events in JavaScript, including:

- Mouse events (click, hover, mouseover, etc.)
- Keyboard events (keydown, keyup, etc.)
- Form events (submit, change, etc.)
- Window events (load, resize, scroll, etc.)
- Custom events (events triggered by your code)

### Event Object

When an event occurs, the browser creates an Event object and passes it as an argument
to your event handler function. This object contains information about the event,
such as the type of event, the target element, and any additional data related
to the event.

## Capturing and Bubbling

![Event Flow Process](https://www.freecodecamp.org/news/content/images/2023/10/bubbling-and-capturing2.png)

JavaScript events follow a capturing and bubbling phase. Events start from the
outermost element and move inward during the capturing phase, then bubble back outward.

- **Event bubbling** is the phase where the event bubbles up from the target
- element all the way to the global window object.

![How event bubbling works](https://www.freecodecamp.org/news/content/images/2023/10/bubbling-and-capturing3.png)

- **Event capturing** occurs when a nested element is clicked, triggering the
  click event of its parent elements before the click of the nested element.
- This phase trickles down from the top of the DOM tree to the target element.
- Event capturing requires setting the third argument of addEventListener to
  the Boolean value of true (default value is false).
- When the third argument of `addEventListener` is set to true, event handlers
  are automatically triggered in the capturing phase.
- With event capturing, the event handler attached to an ancestor element will
  be executed first when an event occurs on a nested element
  within the DOM hierarchy, unlike the default bubbling phase.

![Event Capturing](https://www.freecodecamp.org/news/content/images/2023/10/bubbling-and-capturing4.png)

You can control this behavior using the `capture` parameter:

```js
const grandparent = document.getElementById("grandparent");

// Capture phase
grandparent.addEventListener(
  "click",
  () => {
    console.log("Grandparent captured");
  },
  true
);

// Bubble phase
grandparent.addEventListener("click", () => {
  console.log("Grandparent bubbled");
});
```

In this example, the event listener on the grandparent element captures the event first,
then bubbles it back up. Understanding capturing and bubbling is crucial for
managing event propagation.

## Stopping Propagation

Sometimes you might want to stop an event from propagating further.
You can achieve this using `event.stopPropagation()`:

```javascript
const parent = document.getElementById("parent");

parent.addEventListener("click", (event) => {
  console.log("Parent clicked");
  event.stopPropagation(); // Prevent bubbling
});
```

By calling `stopPropagation()`, you prevent the event from reaching other elements in the DOM hierarchy.

## Once Event Listener

add event listeners that only run once using the `{once: true} option:

```js
const parent = document.getElementById("parent");

parent.addEventListener(
  "click",
  () => {
    console.log("Parent clicked once");
  },
  { once: true }
);
```

## Remove Event Listener

remove event listeners using `removeEventListener`:

```js
const parent = document.getElementById("parent");

function handleClick() {
  console.log("Parent clicked");
  parent.removeEventListener("click", handleClick);
}
parent.addEventListener("click", handleClick);
```

## Event Delegation

Event delegation is a powerful technique for handling events on dynamically
created elements. Instead of attaching event listeners to individual elements,
you attach them to a parent element and check if the event target matches a
specific selector:

```js
document.addEventListener("click", (event) => {
  if (event.target.matches(".myDynamicElement")) {
    console.log("Dynamic element clicked");
  }
});
```

> This way, you can handle events on elements that may not exist at the time of
> attaching the event listener.

## Best Practices

- **Useful Naming:** Give meaningful names to your event handlers to make your
  code more readable and maintainable.

- **Separation of Concerns:** Keep your event handling code separate from your HTML
  and CSS. This improves code organization and makes it easier to maintain.

- **Avoid Inline Handlers:** Instead of using inline event handlers in your HTML
  (e.g., onclick="myFunction()"), attach event listeners programmatically in your
  JavaScript code.

- **Delegate Events:** Use event delegation to handle events on multiple elements
  with a single event listener. This can improve performance, especially for
  large lists or tables.

- **Consider Event Bubbling:** Understand event bubbling, which is the default
  behavior where an event first triggers on the innermost target element and then
  bubbles up through its ancestors. Utilize this behavior effectively in your
  event handling strategies.

- **Remove Event Listeners:** Remove event listeners when they are no longer
  needed to avoid memory leaks and improve performance.

- **Utilize Event Object Properties:** Make use of properties of the event object,
  such as `event.target`, `event.currentTarget`, and `event.type`, to access
  relevant information about the event and its target element.

- **Comment Your Event Handling Code:** Add comments to explain complex event
  handling logic or to provide context for future developers who might work
  on the codebase.

- **Follow the Single Responsibility Principle:** Ensure that each event handler
  performs a single, well-defined task and adheres to the principle of single responsibility.
  This improves code readability, maintainability, and debugging.

### List of References

- [Learn JavaScript KEY EVENTS in 10+ minutes!](https://www.youtube.com/watch?v=q32skvBgxo4)
- [Learn JavaScript MOUSE EVENTS in 10 minutes!](https://www.youtube.com/watch?v=g_vXSKbfUiQ)
