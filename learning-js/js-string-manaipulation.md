## String Manipulation

### String Comparison

String comparison in JavaScript is done using various methods such as `localeCompare()`, and simply comparing the strings using operators like `===`. Here's a brief explanation of each:

#### `localeCompare()`

This method compares two strings in the current locale. It returns a number indicating whether the reference string comes before, after, or is equivalent to the compared string.

```javascript
const str1 = "apple";
const str2 = "banana";
console.log(str1.localeCompare(str2)); // Output: -1 (str1 comes before str2)
```

#### Operator Comparison

Strings can also be compared using operators like ===, which compares both value and type.

#### Unicode

> Unicode is a character encoding standard that assigns a unique numeric value to each character, > including letters, digits, and symbols, across different writing systems and languages. > JavaScript uses Unicode to represent and process string data.

Here are some **key points** about Unicode in JavaScript:

- Characters in JavaScript strings are represented using their Unicode code points.
- Unicode allows for encoding characters beyond the ASCII range, enabling support for a wide range of languages and symbols
- JavaScript methods includes `charCodeAt()` and `String.fromCharCode()` for working with Unicode code points.

#### Regular Expressions

Regular expressions, often abbreviated as **"regex"** are powerful tools for pattern matching and string manipulation in JavaScript. It allows you to search for, extract, and also can be used to replace patterns within strings.

**common use cases for regular expressions:**

- **Validating input:** Regex can be used to ensure that user input matches a specific pattern, such as an email address or phone number.

```js
// Regular expression pattern for validating email addresses
const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

// Function to validate email input
function validateEmail(email) {
  return emailPattern.test(email);
}

// Example usage
const userEmail = "example@email.com";
if (validateEmail(userEmail)) {
  console.log("Email is valid!");
} else {
  console.log("Invalid email!");
}
```

> a regular expression pattern emailPattern which checks for a string that starts (^) and ends ($) with a sequence of characters that do not include whitespace ([^\s@]+), followed by an "@" symbol, then another sequence of characters that do not include whitespace, then a dot ".", and finally another sequence of characters that do not include whitespace.

- **Search and replace:** Regex allows you to find all occurrences of a pattern within a string and replace them with another string.

```js
// Sample string
let text =
  "The quick brown fox jumps over the lazy dog. The quick fox is faster than the lazy dog.";

// Regular expression pattern to search for occurrences of "fox" and replace with "cat"
const regex = /fox/g; // "g" flag indicates global search (find all occurrences)

// Replacement string
const replacement = "cat";

// Perform the search and replace using the replace() method
const newText = text.replaceAll(regex, replacement);

// Output the result
console.log(newText);
```

- **Data extraction**: Regex can extract specific parts of a string, such as extracting numbers or extracting text between delimiters.

```js
// Sample string containing numbers
const text =
  "The price of the product is $25.50 and the shipping cost is $5.75.";

// Regular expression pattern to extract numbers (including decimal numbers)
const numberPattern = /\d+(\.\d+)?/g;

// Extracting numbers from the text using the match() method
const numbers = text.match(numberPattern);

// Output the extracted numbers
console.log(numbers);
```

To learn & practice RegEx

- [https://regexone.com/](https://regexone.com/)
- [https://regexlearn.com/learn](https://regexlearn.com/learn)
- [https://www.freecodecamp.org/news/practical-regex-guide-with-real-life-examples/](https://www.freecodecamp.org/news/practical-regex-guide-with-real-life-examples/)
