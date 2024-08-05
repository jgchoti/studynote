# Express - A Web Framework for Node.js

- Express is a fast, unopinionated, and minimalist web framework for Node.js. 
- It provides robust tools for creating server-side applications and APIs, handling HTTP requests and responses, and managing various other aspects of web application development.

## Why Use Express?

- Minimalist: Express is lightweight and does not come with unnecessary features, allowing developers to build applications with a small footprint.
- Flexible: It provides a thin layer of fundamental web application features, without obscuring Node.js features.
- Extensible: Numerous middleware modules are available to extend its functionality.
- Performance: Built on top of the asynchronous, non-blocking Node.js runtime, Express can handle a large number of simultaneous connections efficiently.

## Setting Up an Express Application

Initialize a Node.js Project:

```bash
npm init -y
```

Install Express:

```bash
npm install express
```

Basic Application Structure:

```javascript
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
    res.send('Hello World!');
});

app.listen(port, () => {
    console.log(`Example app listening at http://localhost:${port}`);
});
```

## Middleware in Express

- Middleware functions are functions that have access to 
  - the request object (req)
  - the response object (res)
  - the next middleware function in the application’s request-response cycle. 

Middleware can:

- Execute any code.
- Make changes to the request and response objects.
- End the request-response cycle.
- Call the next middleware function.

### Example of Middleware:

```javascript
const express = require('express');
const app = express();
const port = 3000;

// Middleware function to log request details
app.use((req, res, next) => {
    console.log(`Request Method: ${req.method}, Request URL: ${req.url}`);
    next();
});

app.get('/', (req, res) => {
    res.send('Hello World!');
});

app.listen(port, () => {
    console.log(`Example app listening at http://localhost:${port}`);
});

```

## Routing in Express

- Routing refers to how an application’s endpoints (URIs) respond to client requests.
- Express provides a simple and flexible way to define routes.

### Basic Routing Example:

```javascript
app.get('/', (req, res) => {
    res.send('Home Page');
});

app.get('/about', (req, res) => {
    res.send('About Page');
});
```

### Route Parameters:

Route parameters are named URL segments that capture the values specified at their position in the URL.

```javascript
app.get('/users/:userId/books/:bookId', (req, res) => {
    res.send(req.params);
});
```

### Handling Different HTTP Methods

Express can handle various HTTP methods such as GET, POST, PUT, DELETE, etc.

Example:

```javascript
app.post('/user', (req, res) => {
    res.send('Got a POST request');
});

app.put('/user', (req, res) => {
    res.send('Got a PUT request at /user');
});

app.delete('/user', (req, res) => {
    res.send('Got a DELETE request at /user');
});
```

## Serving Static Files

Express provides a built-in middleware to serve static files such as images, CSS files, and JavaScript files.

Example:
```javascript

app.use(express.static('public'));
```

> This will serve all files in the public directory at the root URL.

## Error Handling

Error handling middleware functions have four arguments: (err, req, res, next).

Example:

```javascript

app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).send('Something broke!');
});
```

## Working with JSON and URL-encoded Data

Express has built-in middleware to handle JSON and URL-encoded data.

Example:

```javascript

app.use(express.json()); // for parsing application/json
app.use(express.urlencoded({ extended: true })); // for parsing application/x-www-form-urlencoded
```

## Example Application with Express

Here's a more complete example showcasing an Express application with multiple routes, middleware, error handling, and serving static files:

```javascript

const express = require('express');
const path = require('path');
const app = express();
const port = 3000;

// Middleware to log request details
app.use((req, res, next) => {
    console.log(`${req.method} request for '${req.url}'`);
    next();
});

// Middleware to serve static files
app.use(express.static(path.join(__dirname, 'public')));

// Body parser middleware
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Basic route
app.get('/', (req, res) => {
    res.send('Welcome to the Home Page!');
});

// Route with parameters
app.get('/users/:userId', (req, res) => {
    res.send(`User ID: ${req.params.userId}`);
});

// Handling POST request
app.post('/submit', (req, res) => {
    res.send(`Form submitted! Name: ${req.body.name}`);
});

// Error handling middleware
app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).send('Something broke!');
});

app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}/`);
});

```

> In this example:
> Middleware is used to log request details and serve static files from the public directory.
> The body-parser middleware is used to parse JSON and URL-encoded data.
> Routes are defined to handle GET and POST requests.
> An error-handling middleware is included to handle any errors that occur during request processing.
> This example showcases how Express simplifies the development of robust web applications with a clean and modular structure.