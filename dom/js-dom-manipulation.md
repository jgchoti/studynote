# DOM manipulation

## Adding Elements:

Adding elements to a page is simple. We first select the element where we want
to add content,typically using document.querySelector() or similar methods.
For example, to add content to the <body> element, we can use document.body.
Then, we can use the append() method to add elements.

```javascript
// Adding text directly
document.body.append("Hello, world!");

// Adding multiple elements
document.body.append("Hello", " ", "world!");
```

## Creating Elements:

To create an element dynamically, we use the document.createElement() method.
We specify the type of element we want to create, like `<div>`, `<span>`, etc.
Then, we can manipulate and add it to the DOM.

```javascript
// Creating a <div> element
const div = document.createElement("div");
document.body.append(div); // Adding the div to the page
```

## Modifying Text:

We can modify text content inside elements using properties like `innerText` or `textContent`.

```javascript

// Modifying text content
div.innerText = "Hello, world!"; // Sets text content
Manipulating HTML:
```

To manipulate HTML inside an element, we use the`innerHTML` property.

This allows us to set HTML content directly, including tags.

```javascript
// Manipulating HTML content
div.innerHTML = "<strong>Hello, world!</strong>"; // Sets HTML content
```

## Removing Elements:

Removing elements from the DOM is straightforward. We can use methods like `remove()` or `removeChild()`.

```javascript
// Removing elements
div.remove(); // Removes the div from the page
```

## Modifying Attributes:

We can modify attributes of elements using methods like setAttribute() and removeAttribute().

```javascript
// Modifying attributes
div.setAttribute("id", "myDiv"); // Sets attribute
div.removeAttribute("id"); // Removes attribute
```

## Handling Classes:

Manipulating classes is essential for styling elements dynamically.
We use methods like classList.add(), classList.remove(), and classList.toggle().

```javascript
// Handling classes
div.classList.add("myClass"); // Adds class
div.classList.remove("myClass"); // Removes class
div.classList.toggle("active"); // Toggles class
```

## Modifying Styles:

Finally, we can modify CSS styles directly using the style property.

```javascript
// Modifying styles
div.style.color = "red"; // Sets text color
div.style.backgroundColor = "blue"; // Sets background color
```

### List of References

- [Learn DOM Manipulation](https://www.youtube.com/watch?v=y17RuWkWdn8)
