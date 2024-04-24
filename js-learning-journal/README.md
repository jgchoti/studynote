# JavaScript Learning Journal

This learning journal documents my journey through solving JavaScript challenges from several resouces including

- [codewars.com](https://www.codewars.com/users/jgchoti)
- [geeksforgeeks.org](https://www.geeksforgeeks.org/user/jgchoto42h/)
- [edabit.com](https://edabit.com/user/WT4DRCWmoNwZYNnCC)
- [leetcode](https://leetcode.com/jgchoti/)
- [exercism.org](https://exercism.org)

Throughout this journal, I recorded code snippets, and discussed the insights I've gained along the way. It serves as a record of my progress and a resource for reflecting on my learning journey in JavaScript.

---



---


---

## Strings containing numeric parts in ascending order

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

---

## Finds duplicate elements in the array

```js
/**
 * Finds elements occurring more than once in the given array and returns them in ascending order.
 * If no such element is found, returns [-1].
 * @param {number[]} a - The input array containing elements from 0 to N-1.
 * @param {number} n - The size of the array.
 * @returns {number[]} - An array containing elements occurring more than once in ascending order, or [-1] if none found.
 */
function duplicates(a, n) {
  // Sort the array in ascending order
  a = a.sort((a, b) => a - b);

  // Initialize a map to store the count of occurrences of each element
  const countMap = new Map();

  // Populate the countMap with the count of occurrences of each element
  a.forEach((num) => {
    countMap.has(num)
      ? countMap.set(num, countMap.get(num) + 1)
      : countMap.set(num, 1);
  });

  // Filter out elements with occurrences greater than 1
  let occurrenceNumber = a.filter((num) => countMap.get(num) > 1);

  // Convert the filtered array to a Set to remove duplicates
  occurrenceNumber = new Set(occurrenceNumber);

  // Check if the Set is not undefined, and return the elements in ascending order
  return occurrenceNumber !== undefined ? [...occurrenceNumber] : [-1];
}
```

**Approach:**

1. The array a is sorted in ascending order using the `sort()` method.
2. A Map named `countMap` is initialized to store the count of occurrences of each element in the array.
3. Using `forEach()`, each element of the array is iterated, and its count is updated in the countMap.

   1. `countMap.has(num)`: This checks whether the num is already a key in the countMap.
      1. `countMap.get(num) + 1`: It fetches the current count of num and increments it by 1.
      2. `countMap.set(num, countMap.get(num) + 1)` it sets this new count as the value for the key `num` using `countMap.set(num, ...).`

4. The filtered array is converted to a Set to remove duplicate elements.
5. The set is converted back to an array using the spread operator [...occurrenceNumber], and returned. If no duplicate elements are found, [-1] is returned.
