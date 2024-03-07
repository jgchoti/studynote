# Into Programming

summary note from [You Don't Know JS: Up & Going - hapter 1: Into Programming](https://github.com/getify/You-Dont-Know-JS/blob/1st-ed/up%20%26%20going/ch1.md)

### Basics of Code

- **Code:** A set of special instructions that instruct the computer to perform tasks.
- **Computer Language:** Defines the valid format and combinations of instructions (syntax).
- **Statements:** Groups of words, numbers, and operators that perform specific tasks.

### Variables and Expressions

- **Variables:** Symbolic placeholders for values.
- **Expressions:** Combinations of variables, literals, and operators.
- **Operators:** Symbols like `=`, `*` for operations.

### Example Statement

```javascript
a = b * 2;
```

- `a` and `b` are variables, representing values.
- `2` is a literal value expression.
- `b` is a variable expression, retrieving its current value.
- `b * 2` is an arithmetic expression, performing multiplication.
- `a = b * 2` is an assignment expression, storing the result in variable a.

> tells the computer, roughly, to get the current value stored in the variable `b`,
> multiply that value by 2, then store the result back into another variable we call `a`

### Program Execution

- **_Executing_**: Running the program.
- **_Interpreting_**: Running line by line.
- **_Compiles_**: Runs ahead of time. JavaScript is compiled.

### Output

- `console.log(b);` prints `b` value to the console.
- `alert(b);` shows a pop-up alert with `b` value.

### Input

- `age = prompt("Please tell me your age:");` captures user input.

### Operators

- Arithmetic, increment/decrement, equality, comparison, logical, and assignment operators.
  - **_Math_**: `+` (addition), `-` (subtraction), `*` (multiplication), and `/` (division)
  - **_Increment/Decrement_**: `++` (increment), `--` (decrement), as in `a++` (similar to `a = a + 1`).
  - **_Equality_**: - `==` (loose equals) - `===` (strict-equals) - `!=` (loose not-equals) - `!==` (strict not-equals)
  - **_Comparison_**: `<` (less than), `>` (greater than), `<=` (less than or loose-equals), `>=` (greater than or loose-equals), as in `a <= b`
  - **_Logical_**: `&&` (and), `||` (or), as in `a || b` that selects either `a` or `b`.
- The `=` equals operator is used for _assignment_
  - _Right-hand side_ (source value)
  - _Left-hand side_ (target variable).

### Values and Types

- Primitive values are built-in types in JavaScript.

### Converting Between Types

- Explicit and implicit coercion.
- _explicit_ coercion
  - `Number(..)` (a built-in function)
- _implicit_ coercion
  - Example: Using `==` converts the left-hand side from string to number for comparison.

### Code Comments

- Guidelines for effective comments.
- `//` for one-line comments and `/* .. */` for multiline comments in JavaScript.

### Variables

- Dynamic typing in JavaScript allows variables to hold any type.
- Constants are variables with values that don't change.
- Constants are often capitalized with underscores between words.

### Blocks

- JavaScript uses `{ .. }` for blocks.

### Conditionals

- `if` statements for conditional execution.

### Loops

- Iterations using `while` and `do..while` loops.
- Iterations typically start from `0` in programming languages.

### Functions

- Functions take arguments and can return values.

### Scope

- Lexical scope determines variable accessibility within functions.
- Only code inside that function can access that function's scoped variables.
- code in one scope can access variables of either that scope or any scope outside of it.

### Practice

#### Phone Purchase Program

1. **Purchase Loop:**

   - Use a loop to buy phones and accessories until out of money or reaching spending threshold.

2. **Calculate Purchase Amount:**

   - Calculate total purchase amount, including phones, accessories, and tax.

3. **Print Formatted Purchase Amount:**

   - Print the calculated purchase amount in a properly formatted manner.

4. **Check Affordability:**

   - Compare purchase amount with bank account balance to determine affordability.

5. **Constants and Variables:**

   - Set up constants for tax rate, phone price, and accessory price.
   - Create a variable for bank account balance.

6. **Functions:**

   - Define functions for calculating tax.
   - Define a function for formatting the price with a "$" and rounding to two decimal places.

7. **Bonus Challenge:**
   - Incorporate user input, such as prompting for the bank account balance, and spending threshold.
   - Encourage creativity and have fun with the implementation.

```javascript
const TAX_RATE = 0.21;
const PHONE_PRICE = 350;
const ACCESSORY_PRICE = 5;

function displayPurchaseDetailsWithAddition(
  phonePriceWithTax,
  bankAccountBalance,
  totalPhoneCost
) {
  if (phonePriceWithTax < bankAccountBalance) {
    console.log(
      "You have $" +
        bankAccountBalance.toFixed(2) +
        " in your bank account. You can not afford a phone priced at $" +
        PHONE_PRICE.toFixed(2) +
        " with tax"
    );
    let additionalBalance = phonePriceWithTax - bankAccountBalance;
    console.log(
      "You will need an additional  $" +
        additionalBalance.toFixed(2) +
        " in your bank account to buy a phone"
    );
  } else {
    console.log(
      "You have $" +
        bankAccountBalance.toFixed(2) +
        " in your bank account. You can afford a phone priced at $" +
        PHONE_PRICE.toFixed(2) +
        " with tax but you can not afford to buy an accessory for a phone"
    );
    let additionalBalance = totalPhoneCost - bankAccountBalance;
    console.log(
      "You will need an additional  $" +
        additionalBalance.toFixed(2) +
        " in your bank account to buy a phone with an accessory "
    );
  }
}
function displayPurchaseAdjustThreshold(
  phonesToBuy,
  bankAccountBalance,
  totalPhoneCost,
  spendingThreshold
) {
  bankAccountBalance = bankAccountBalance - phonesToBuy * totalPhoneCost;
  console.log(
    `Warning: You will exceed your spending threshold of $${spendingThreshold.toFixed(2)}! But you can buy ${phonesToBuy} phones with an accessory for each phone, and you will have $${bankAccountBalance.toFixed(2)} left in your bank account.`
  );
}

function displayPurchaseDetails(
  phonesToBuy,
  bankAccountBalance,
  totalPhoneCost
) {
  bankAccountBalance = bankAccountBalance - phonesToBuy * totalPhoneCost;
  if (phonesToBuy === 1) {
    console.log(
      `You can buy a phone with an accessory, and you will have $${bankAccountBalance.toFixed(2)} left in your bank account.`
    );
  } else {
    console.log(
      `You can buy ${phonesToBuy} phones with an accessory for each phone, and you will have $${bankAccountBalance.toFixed(2)} left in your bank account.`
    );
  }
}

function toAffordPhoneWithAccessory(bankAccountBalance, totalPhoneCost) {
  return totalPhoneCost <= bankAccountBalance;
}

function calculateTax(price) {
  let priceWithTax = price * (1 + TAX_RATE);
  return priceWithTax;
}

function toBuyAccessory(bankAccountBalance, spendingThreshold) {
  let accessoryPriceWithTax = parseFloat(
    calculateTax(ACCESSORY_PRICE).toFixed(2)
  );
  let phonePriceWithTax = parseFloat(calculateTax(PHONE_PRICE).toFixed(2));
  let totalPhoneCost = phonePriceWithTax + accessoryPriceWithTax;
  let maxPhonesInBalance = Math.floor(bankAccountBalance / totalPhoneCost);
  let maxPhonesInThreshold = Math.floor(spendingThreshold / totalPhoneCost);

  if (toAffordPhoneWithAccessory(bankAccountBalance, totalPhoneCost)) {
    if (maxPhonesInThreshold < maxPhonesInBalance) {
      let phonesToBuy = maxPhonesInBalance;
      displayPurchaseAdjustThreshold(
        phonesToBuy,
        bankAccountBalance,
        totalPhoneCost,
        spendingThreshold
      );
    } else if (maxPhonesInThreshold === maxPhonesInBalance) {
      let phonesToBuy = maxPhonesInThreshold;
      displayPurchaseDetails(phonesToBuy, bankAccountBalance, totalPhoneCost);
    } else {
      let phonesToBuy = maxPhonesInBalance;
      displayPurchaseDetails(phonesToBuy, bankAccountBalance, totalPhoneCost);
    }
  } else {
    displayPurchaseDetailsWithAddition(
      phonePriceWithTax,
      bankAccountBalance,
      totalPhoneCost
    );
  }
}

function toBuyPhone(bankAccountBalance, spendingThreshold) {
  let phonePriceWithTax = parseFloat(calculateTax(PHONE_PRICE).toFixed(2));

  if (phonePriceWithTax <= bankAccountBalance) {
    toBuyAccessory(bankAccountBalance, spendingThreshold);
  } else {
    displayPurchaseDetailsWithAddition(phonePriceWithTax, bankAccountBalance);
  }
}

function inputBankAccount() {
  let bankAccountBalance = prompt("Please input your bank account balance:");
  let spendingThreshold = prompt("Please input your spending threshold:");

  bankAccountBalance = parseFloat(bankAccountBalance);
  spendingThreshold = parseFloat(spendingThreshold);

  if (
    isNaN(bankAccountBalance) ||
    bankAccountBalance == " " ||
    bankAccountBalance === null
  ) {
    console.log("Invalid input.");
    inputBankAccount();
  } else {
    if (
      isNaN(spendingThreshold) ||
      spendingThreshold == " " ||
      spendingThreshold === null
    ) {
      spendingThreshold = 0;
    }
    toBuyPhone(bankAccountBalance, spendingThreshold);
  }
}

inputBankAccount();
```

This chapter provides a comprehensive introduction to programming concepts, JavaScript syntax, and fundamental constructs. It covers variables, expressions, operators, control flow, functions, and more, laying a strong foundation for readers new to programming or JavaScript.
