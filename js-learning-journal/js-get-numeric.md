# Strings containing numeric parts in ascending order

1. Retrieve numeric parts iterates through each character of the string str to checks if the character is a number using `isNaN(parseInt(str[i]))`.
   1. If it's a number, it appends it to the `numericPart` string.
   2. When a non-numeric character is encountered, the loop breaks, and
   3. the function returns the numericPart string.

```js
/**
 * Extracts the numeric part from a given string.
 * @param {string} str - The input string from which to extract the numeric part.
 * @returns {string} The numeric part of the input string. If no numeric part is found, an empty string is returned.
 */
function getNumericPart(str) {
  let numericPart = "";
  for (let i = 0; i < str.length; i++) {
    if (!isNaN(parseInt(str[i]))) {
      numericPart += str[i];
    } else {
      // If a non-numeric character is encountered, break the loop
      break;
    }
  }
  return numericPart;
}
```

2. use `.sort()` to return the sorted array of strings

```js
let wordsArray = ["word2", "word10", "word1", "word20", "word5"];

/**
 * Sorts an array of strings based on their numeric parts.
 * @param {string[]} arr - An array of strings to be sorted.
 * @returns {string[]} The sorted array of strings.
 */
function sortByNumericPart(arr) {
  return arr.sort((a, b) => {
    const numA = parseInt(getNumericPart(a));
    const numB = parseInt(getNumericPart(b));
    return numA - numB;
  });
}

let order = sortByNumericPart(wordsArray);

console.log(order); // Output: ["word1", "word2", "word5", "word10", "word20"]
```

#### OR USE RegEx with `.match()`

```js
/**
 * Sorts an array of strings based on their numeric parts using regular expressions.
 * @param {string[]} arr - An array of strings to be sorted.
 * @returns {string[]} The sorted array of strings.
 */
function sortByNumericPart(arr) {
  return arr.sort((a, b) => {
    const numA = parseInt(a.match(/\d+/)[0]);
    const numB = parseInt(b.match(/\d+/)[0]);
    return numA - numB;
  });
}
```

> - In this function, `a.match(/\d+/)` and `b.match(/\d+/)` are used to extract the numeric parts of strings a and b, respectively.
> - The `parseInt()` function is then used to convert these numeric parts into integers for comparison.
