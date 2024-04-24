# Digit Swapping function without converting it into a string.

```js
/**
 * Determines if a number is the largest possible number that can be obtained by swapping its digits.
 * @param {number} num - The input number to check.
 * @returns {boolean} Returns true if the input number is greater than or equal to the largest possible number obtained by swapping its digits; otherwise, returns false.
 */
function largestSwap(num) {
  let originNum = num;
  let swapNumber = 0;
  while (num > 0) {
    let digit = num % 10;
    swapNumber = swapNumber * 10 + digit;
    num = Math.floor(num / 10);
  }
  return originNum >= swapNumber;
}
```

> - Used a while loop to iterate through each digit of the number.
> - Inside the loop, extracted the last digit of num using modulo (%) operator and added it to swapNumber.
> - Updated num to remove the last digit using Math.floor(num / 10).
