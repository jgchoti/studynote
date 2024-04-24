# Finds duplicate elements in the array

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
