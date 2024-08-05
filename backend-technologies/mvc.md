# MVC Architecture in Node.js

## Model-View-Controller (MVC) Overview

![Model-View-Controller (MVC) Overview](https://www.freecodecamp.org/news/content/images/2021/04/MVC3.png)

- **Model** : Responsible for maintaining data. Handles data logic and communicates with the database.
- **View** : Responsible for data representation. Generates the user interface (UI) for the user. Communicates only with the controller, not directly with the model.
- **Controller**: Acts as an intermediary between the view and the model. Handles user input and interaction, updating the model and view as necessary.

## Updating a Function in MVC Node.js

- Update EJS Template (home.ejs):
  
```html

<form action="/book/<%= book.id %>?_method=DELETE" method="POST">
    <button type="submit">Delete</button>
</form>
```

## Update Backend Controller (homeControllers):

```javascript

deleteBook: (req, res) => {
    const { id } = req.params;
    Book.deleteBook(id);
    res.redirect('/');
},
```

Modify Book Model (models/book.js):

```javascript
static deleteBook(id) {
    const index = books.findIndex((book) => book.id === id);
    if (index !== -1) {
        books.splice(index, 1);
    }
}
```

## Configure Route for Delete Operation (routes/home.js):

```javascript
// Delete a book
router.delete('/book/:id', homeControllers.deleteBook);
Use Method-Override for DELETE:
bash
Copy code
npm install method-override
Update your server setup (server.js):
javascript
Copy code
import methodOverride from 'method-override';

// Set up method-override middleware
app.use(methodOverride('_method')); 

```

## Node.js Core Modules and APIs

**events Module**
Provides EventEmitter objects used to assign listener functions triggered on specified events.

**Buffer Object**
Represents a static amount of memory that can’t be resized.

Methods:
`.alloc(size, fill)`: Creates a buffer of specified size filled with the given value.
`.toString()`: Converts the buffer content to a string.
`.from()`: Creates a buffer from a specified string, array, or another buffer.
`.concat()`: Joins all buffers in the specified array into one buffer.

**timers Module**
Contains scheduling functions such as `setTimeout()`, `setInterval()`, and `setImmediate()`.

`setImmediate()`
Executes the specified callback function after the current event loop has completed.