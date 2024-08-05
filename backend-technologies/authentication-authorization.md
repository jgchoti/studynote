# Authentication & Authorization

![Authentication & Authorization](https://developer.okta.com/assets-jekyll/blog/node-token-auth/token-authentication-flow-69804c12334715c597128cd9273bca5e32ed516b62987902310efc54d1840a40.png)

- Authentication and authorization are essential for securing Node.js applications
- ensuring users are properly identified and granted appropriate permissions.


---

## Authentication

- Authentication verifies a user's identity using credentials such as a username and password. 
- It often involves checking if the credentials match stored data and issuing tokens or sessions upon successful verification.

### Password Matching

- To compare passwords securely, you can use the `bcryptjs` library, which hashes passwords and checks them against stored hashes.

Example of Password Matching:

```javascript
import bcrypt from 'bcryptjs';

const matchPasswords = (password, hashedPassword) => {
    return bcrypt.compare(password, hashedPassword);
};

export default matchPasswords;
```

`bcrypt.compare(password, hashedPassword)`: Compares a plain password with a hashed password and returns a promise that resolves to true if they match, otherwise false.

## Authorization

Authorization controls access to resources based on user permissions or roles. It ensures that only authorized users can access certain routes or perform specific actions.

### Token Verification

- Use JSON Web Tokens (JWT) to manage user sessions and verify their authenticity. 
- Tokens are typically stored in cookies or local storage and are used to authenticate user requests.

Example of Token Verification Middleware:

```javascript

import jwt from 'jsonwebtoken';

const verifyToken = (req, res, next) => {
    const token = req.cookies.token;
    if (token) {
        jwt.verify(token, process.env.TOKEN_ACCESS_SECRET, (err, data) => {
            if (err) {
                res.status(498).json({ message: 'Token is not valid' });
            } else {
                // Optionally attach user data to the request object
                req.user = data;
                next();
            }
        });
    } else {
        res.status(498).json({ message: 'Token is not valid' });
    }
};

export default verifyToken;
```

- `jwt.verify(token, process.env.TOKEN_ACCESS_SECRET, callback)`: Verifies the JWT token using a secret key. 
  - If the token is valid, the callback receives the decoded data. 
  - If not, an error is returned.

- `req.cookies.token`: Retrieves the token from the request cookies.

---

### Securing Authentication and Authorization

#### Hash Passwords

Ensure passwords are hashed using libraries like `bcryptjs` before storing them in the database.

Hashing Password Example:
```js
import bcrypt from 'bcryptjs';

// Hash a password
const hashPassword = async (password) => {
    try {
        const salt = await bcrypt.genSalt(10); // Generate a salt
        const hashedPassword = await bcrypt.hash(password, salt); // Hash the password with the salt
        return hashedPassword;
    } catch (error) {
        console.error('Error hashing password:', error);
        throw new Error('Password hashing failed');
    }
};

// Compare a password with a hashed password
const comparePasswords = async (password, hashedPassword) => {
    try {
        const isMatch = await bcrypt.compare(password, hashedPassword);
        return isMatch;
    } catch (error) {
        console.error('Error comparing passwords:', error);
        throw new Error('Password comparison failed');
    }
};

export { hashPassword, comparePasswords };
```

- `bcrypt.genSalt(rounds`): Generates a salt with the specified number of rounds.
- `bcrypt.hash(password, salt)`: Hashes the password using the salt.
- `bcrypt.compare(password, hashedPassword)`: Compares a plain password with a hashed password.

#### Secure Tokens

Use environment variables to keep secrets like `TOKEN_ACCESS_SECRET` secure and ensure tokens are sent over HTTPS.

```js
import jwt from 'jsonwebtoken';

// Middleware to verify JWT tokens
const verifyToken = (req, res, next) => {
    const token = req.cookies.token;
    if (token) {
        jwt.verify(token, process.env.TOKEN_ACCESS_SECRET, (err, decoded) => {
            if (err) {
                return res.status(498).json({ message: 'Token is not valid' });
            }
            req.user = decoded; // Add the decoded user data to the request object
            next();
        });
    } else {
        res.status(401).json({ message: 'No token provided' });
    }
};

export default verifyToken;
```

- `jwt.verify(token, secret, callback)`: Verifies the token using the secret key
- Environment Variables: Use .env files or other secure methods to manage secrets.

#### Error Handling

Implement robust error handling to manage unauthorized access and token verification failures gracefully.

```js
import { hashPassword, comparePasswords } from '../utils/authUtils.js'; // Utility functions for password handling
import query from '../config/db.js'; // Database query utility

const userControllers = {
    // Example of user registration with password hashing
    registerUser: async (req, res) => {
        const { username, password } = req.body;
        try {
            if (!username || !password) {
                return res.status(400).json({ error: 'Username and password are required' });
            }
            const hashedPassword = await hashPassword(password);
            const sql = 'INSERT INTO users (username, password) VALUES (?, ?)';
            await query(sql, [username, hashedPassword]);
            res.status(201).json({ message: 'User registered successfully' });
        } catch (error) {
            console.error('Error registering user:', error);
            res.status(500).json({ error: 'Error registering user' });
        }
    },

    // Example of user login with password comparison
    loginUser: async (req, res) => {
        const { username, password } = req.body;
        try {
            if (!username || !password) {
                return res.status(400).json({ error: 'Username and password are required' });
            }
            const sql = 'SELECT password FROM users WHERE username = ?';
            const result = await query(sql, [username]);
            if (result.length === 0) {
                return res.status(404).json({ error: 'User not found' });
            }
            const isMatch = await comparePasswords(password, result[0].password);
            if (!isMatch) {
                return res.status(401).json({ error: 'Invalid credentials' });
            }
            const token = jwt.sign({ username }, process.env.TOKEN_ACCESS_SECRET, { expiresIn: '1h' });
            res.cookie('token', token, { httpOnly: true, secure: true }); // Set token in a secure cookie
            res.status(200).json({ message: 'Login successful' });
        } catch (error) {
            console.error('Error logging in user:', error);
            res.status(500).json({ error: 'Error logging in user' });
        }
    }
};

export default userControllers;
```

- **Password Hashing and Comparison**: Ensure passwords are securely hashed and compared.
- **Token Management**: Issue and verify tokens securely, and manage errors effectively.
- **Error Responses**: Return meaningful error messages and status codes.