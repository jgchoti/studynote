# DOM manipulation

## Navigating the DOM Tree with Node Properties

### `parentNode` and `parentElement`

- **`parentNode`** returns the parent element of the specified child node.
  It allows you to traverse up the DOM tree from a child node to its parent node.

```javascript
const child = document.getElementById("child");
const parentElement = child.parentNode;
```

- **`parentElement`** returns the parent element node of the specified element.

```javascript
const parentElement = element.parentElement;
```

### `childNodes`

Returns a NodeList of all child nodes, including elements, text, and comments, of the specified node.

```javascript
const childNodes = parent.childNodes;
```

### `firstElementChild`

This property returns the first child element node of the specified parent element.
It differs from `firstChild`, which can return any type of node (including text
nodes and comment nodes).
Using firstElementChild ensures that you specifically get the first child element
node.

```javascript
const parent = document.getElementById("parent");
const firstChildElement = parent.firstElementChild;
```

### `lastElementChild`

Similar to `firstElementChild`, this property returns the last child element
node of the specified parent element. It ensures that you get the last child
element node specifically.

```javascript
const parent = document.getElementById("parent");
const lastChildElement = parent.lastElementChild;
```

### `children[i]`

The children property returns a live HTMLCollection of all child elements of
the specified parent element. You can access individual child elements using
array-like notation, where i represents the index of the child element you
want to access.

```javascript
const parent = document.getElementById("parent");
const thirdChildElement = parent.children[2]; // Accessing the third child element
```

### `nextSibling` and `previousSibling`

- **`nextSibling`:** returns the next sibling node of the specified node in
  the DOM tree.
- **`previousSibling`:** returns the previous sibling node of the specified
  node in the DOM tree.

```javascript
const nextSibling = element.nextSibling;
const previousSibling = element.previousSibling;
```

### `querySelector()`

Returns the **first** element that matches a specified CSS selector within the specified node.

```javascript
const element = parent.querySelector(selector);
```

### `querySelectorAll()`

Returns a static NodeList representing a list of elements that match the
specified group of selectors within the specified node.

```javascript
const elements = parent.querySelectorAll(selectors);
```

### `closest()`

Returns the closest ancestor of the specified element that matches a specific
CSS selector or null if no such ancestor exists.

```javascript
const ancestor = element.closest(selector);
```

## Adding Elements

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

### `appendChild()`

Appends a node as the last child of a specified parent node.
It's often used to add newly created elements to the DOM hierarchy.

```javascript
const paragraph = document.createElement("p");
paragraph.textContent = "This is a paragraph appended as the last child.";
const parentDiv = document.getElementById("parent");
parentDiv.appendChild(paragraph);
```

### `insertBefore():`

Inserts a node before a specified child node within a parent node. It provides
more control over the positioning of new elements compared to appendChild().

```javascript
const newParagraph = document.createElement("p");
newParagraph.textContent =
  "This is a paragraph inserted before the first child.";
const parentDiv = document.getElementById("parent");
const firstChild = parentDiv.firstChild;
parentDiv.insertBefore(newParagraph, firstChild);
```

## Creating Elements

To create an element dynamically, we use the document.createElement() method.
We specify the type of element we want to create, like `<div>`, `<span>`, etc.
Then, we can manipulate and add it to the DOM.

```javascript
// Creating a <div> element
const div = document.createElement("div");
document.body.append(div); // Adding the div to the page
```

## Modifying Text

We can modify text content inside elements using properties like `innerText` or `textContent`.

```javascript

// Modifying text content
div.innerText = "Hello, world!"; // Sets text content
Manipulating HTML:
```

### `textContent`

Sets or returns the textual content of a node and its descendants. Unlike `innerHTML`,
it does not interpret the content as HTML, making it safer against injection attacks.

```javascript
const paragraph = document.createElement("p");
paragraph.textContent =
  "This is a paragraph with <strong>strong</strong> content.";
document.body.appendChild(paragraph);
```

### `innerHTML`

Allows setting or getting the HTML content of an element.
It can contain HTML tags, making it useful for dynamically
updating complex content structures.

```javascript
// Manipulating HTML content
div.innerHTML = "<strong>Hello, world!</strong>"; // Sets HTML content
```

## Removing Elements

Removing elements from the DOM is straightforward. We can use methods like `remove()` or `removeChild()`.

```javascript
// Removing elements
div.remove(); // Removes the div from the page
```

## Modifying Attributes

We can modify attributes of elements using methods like setAttribute() and removeAttribute().

```javascript
// Modifying attributes
div.setAttribute("id", "myDiv"); // Sets attribute
div.removeAttribute("id"); // Removes attribute
```

## Handling Classes

Manipulating classes is essential for styling elements dynamically.
We use methods like classList.add(), classList.remove(), and classList.toggle().

```javascript
// Handling classes
div.classList.add("myClass"); // Adds class
div.classList.remove("myClass"); // Removes class
div.classList.toggle("active"); // Toggles class
```

## Modifying Styles

Finally, we can modify CSS styles directly using the style property.

```javascript
// Modifying styles
div.style.color = "red"; // Sets text color
div.style.backgroundColor = "blue"; // Sets background color
```

### List of References

- [Learn DOM Manipulation](https://www.youtube.com/watch?v=y17RuWkWdn8)
