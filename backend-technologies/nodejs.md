# Introduction to Node.js

## JavaScript Limitations and Node.js

- JavaScript was originally designed for browsers and had limitations in interacting with the system.
- Node.js is a platform that allows JavaScript to interact with the file system and other aspects of the computer environment.

## File System Module (fs)

- fs is short for the file system, allowing you to work with the file system on your computer.

Example usage:

```javascript
import fs from 'fs';
import path, { dirname } from 'path';
import { fileURLToPath } from 'url';

// Get the current module's directory path
const __filename = fileURLToPath(import.meta.url);
const PATH = dirname(__filename);
```

> Module Imports:

> `fs` :This module provides an API for interacting with the file system.

> `path`: This module provides utilities for working with file and directory paths.

> `fileURLToPath`and `dirname`: Utilities to get the current file's path and directory name, respectively.

> Get the Current Module's Directory Path:

> **__filename**: Converts the current module's URL to a file path.

> **PATH**: Extracts the directory name from the file path.

### Asynchronous File Operations

Asynchronous file operations do not block the event loop, allowing other code to run while waiting for the file system operations to complete.

```javascript
// Asynchronous File Operations:
const nameToSave = 'John Doe';
const filePath = path.join(PATH, 'name.txt');
```

> `nameToSave`: The content to be written to the file.

> `filePath`: The full path where the file will be saved, combining the current directory and the file name (name.txt).

### Write to the file

```js
fs.writeFile(filePath, nameToSave, 'utf8', (err) => {
    if (err) {
        console.error(err);
    }
    console.log('File saved!');
});
```

> `fs.writeFile`: Writes data to a file, replacing the file if it already exists.

> `filePath`: Path to the file.

> `nameToSave`: Data to be written.

> `utf8`: Encoding type.

> Callback function: Called after the write operation completes. If there's an error, it logs the error; otherwise, it logs "File saved!".


### Read from the file

```js
fs.readFile(filePath, 'utf8', (err, data) => {
    if (err) {
        console.error(err);
    }
    console.log('Read file', data);
});
```

> `fs.readFile`: Reads the contents of a file

> `filePath`: Path to the file.

> `utf8`: Encoding type.

> Callback function: Called after the read operation completes. If there's an error, it logs the error; otherwise, it logs the file contents.

### Append content to the file

```js
const contentToAppend = ' This is some additional content.';
fs.appendFile(filePath, contentToAppend, 'utf8', (err) => {
    if (err) {
        console.error(err);
    } else {
        console.log('Appended to a file successfully!');
    }
});
```

> `fs.appendFile`: Appends data to a file. If the file does not exist, it creates a new file.

> `filePath`: Path to the file.

> `contentToAppen`d`: Data to be appended.

> `utf8`: Encoding type.

> Callback function: Called after the append operation completes. If there's an error, it logs the error; otherwise, it logs "Appended to a file successfully!".

### Delete a file

```js
fs.unlink(filePath, (err) => {
    if (err) {
        console.error('Error deleting file:', err);
    } else {
        console.log('File deleted successfully!');
    }
});
```

- `fs.unlink`: Deletes a file.
  
- `filePath`: Path to the file.
  
- Callback function: Called after the delete operation completes. If there's an error, it logs the error; otherwise, it logs "File deleted successfully!".


## Synchronous File Operations

Synchronous file operations block the event loop, meaning no other code can run until the file system operations complete. These are generally used for simpler scripts or during startup/shutdown sequences where blocking is acceptable.


### Write to the File Synchronously

```
try {
    fs.writeFileSync(filePath, 'This is a synchronous write operation.');
    console.log('File written synchronously');
} catch (err) {
    console.error(err);
}
```

> `fs.writeFileSync`: Synchronously writes data to a file, replacing the file if it already exists.

> `filePath`: Path to the file.

> `Data`: 'This is a synchronous write operation.'

> `try/catch`: Used to handle errors. If there's an error, it logs the error; otherwise, it logs "File written synchronously".


### Read from the File Synchronously

```
try {
    const data = fs.readFileSync('example.txt', 'utf-8');
    console.log('File contents synchronously:', data);
} catch (err) {
    console.error(err);
}
```

> `fs.readFileSync`: Synchronously reads the contents of a file.

> `filePath`: Path to the file ('example.txt').

> `utf8`: Encoding type.

> `try/catch`: Used to handle errors. If there's an error, it logs the error; otherwise, it logs the file contents.


### Append Content to the File Synchronously

```
try {
    fs.appendFileSync('example.txt', '\nThis is an appended line.');
    console.log('File appended synchronously');
} catch (err) {
    console.error(err);
}
```

> `fs.appendFileSync`: Synchronously appends data to a file. If the file does not exist, it creates a new file.

> `filePath`: Path to the file ('example.txt').

> `Data`: '\nThis is an appended line.'

> `try/catch`: Used to handle errors. If there's an error, it logs the error; otherwise, it logs "File appended synchronously".

### Delete a File Synchronously

```
try {
    fs.unlinkSync('example.txt');
    console.log('File deleted synchronously');
} catch (err) {
    console.error(err);
}
```

> `fs.unlinkSync`: Synchronously deletes a file.

> `filePath`: Path to the file ('example.txt').

> `try/catch`: Used to handle errors. If there's an error, it logs the error; otherwise, it logs "File deleted synchronously".


## Node.js Debugger Configuration
Setting Up Debugging in Node.js Projects

- **Step 1: Prepare for Debugging**

  - Click on the "Run" button in your development environment, followed by Add Configuration.
  - This action will create a hidden folder named .vscode with a launch.json file.

- **Step 2: Configure launch.json**
  - Content for launch.json:

```json

{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "skipFiles": [
        "<node_internals>/**"
      ],
      "program": "${file}"
    }
  ]
}
```

> Understanding the Configuration:

> "type": "node" specifies that the debugger is set up for Node.js.

> "request": "launch" indicates that this configuration launches the debugger.

> "skipFiles" allows skipping specific internal Node.js files.

> "program": "${file}" defines the entry point for debugging.
