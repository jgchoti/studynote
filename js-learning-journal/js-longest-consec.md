
# Longest consecutive sequence from an array

```js
/**
 * Finds the longest consecutive sequence of k strings concatenated together from the given array.
 * @param {string[]} strarr - An array of strings.
 * @param {number} k - The number of consecutive strings to concatenate.
 * @returns {string} The longest consecutive sequence of k strings concatenated together. If multiple sequences have the same length, the first one encountered is returned. If k is less than or equal to 0 or greater than the length of strarr, an empty string is returned.
 */
function longestConsec(strarr, k) {
  let longest = "";
  for (let i = 0; k > 0 && i <= strarr.length - k; i++) {
    const tempArray = strarr.slice(i, i + k);
    const tempStr = tempArray.join("");
    if (tempStr.length > longest.length) {
      longest = tempStr;
    }
  }
  return longest;
}

const strarr = ["aa", "bb", "ccc", "dddd", "eee"];
const k = 2;
console.log(longestConsec(strarr, k));
// "cccdddd"
```

> - Sliced strarr to get a temporary array of k consecutive strings and assign to `tempArray`
> - Joined the temporary array (`tempArray`) into a single string tempStr(`tempStr`)
> - Compared the length of `tempStr` with the current `longest` string
> - Updated `longest` if `tempStr` is longer.
