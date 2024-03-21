# Pure Functions

## Introduction to Pure Functions:

- Pure functions are a fundamental concept in functional programming.
- They result in clean, predictable, and testable code.
- Pure functions are decoupled and independent, making them easy to manage and reuse.

## Rules of Pure Functions:

### Same Input, Same Output:

- Pure functions produce identical output for the same input.
- Known as referential transparency, enabling predictability.
- Replaceable by their output, ensuring consistency.

### No Side Effects:

- Pure functions do not modify external state or have side effects.
- They do not mutate data or rely on external dependencies such as databases, APIs, or the DOM.
- Accessing global variables or changing state outside the function makes it impure.

## Examples of Pure Functions:

- **Addition Function:**
  - `add(a, b)` always returns the sum of a and b.
- **String Concatenation Function:**

  - `fullName(firstName, lastName)` always returns the concatenation of firstName and lastName.

- **Higher-Order Functions:**
  - Functions like `filter`, `map`, and `reduce` are examples of pure functions commonly used in functional programming.
  - They operate on arrays without modifying the original data.

## Refactoring Impure Functions to Pure Functions:

- **Avoid Mutations:**

  - Impure functions should not modify external data.
  - Refactor functions to return new data instead of mutating existing data.

- **Parameterization:**

  - Pure functions should have at least one parameter.
    - Scenarios where a pure function doesn't require any parameters
        - Functions that always return the same value regardless of any input.
          
          ```javascript
          function returnConstant()
          return 42;
          }
          ```
      
      - Functions operating solely on external state (such as global variables or environment variables)
        
           ```javascript
        const externalState = 10;
           function pureFunctionWithoutParameters() {
           return externalState * 2;
           }
          ```
  
  - Parameters should be immutable and not modified within the function.

- **Return Values:**
  - Pure functions always return a value.
  - Not returning anything indicates impurity.

## Benefits of Pure Functions:

- **Clean and Predictable Code:**
  - Pure functions lead to cleaner and more predictable codebases.
- **Ease of Testing and Debugging:**
  - Pure functions are easier to test as they produce consistent results.
  - Debugging is simplified due to the absence of side effects.
- **Decoupled and Reusable:**
  - Pure functions are decoupled from the rest of the application, making them easier to reuse and maintain.

## Conclusion:

- While not every function needs to be pure, understanding and using pure functions improves code quality and maintainability.
- Following the rules of pure functions results in more robust and scalable applications.
- Functional programming principles, including pure functions, provide valuable tools for developers to write efficient and maintainable code.

---
#### Ref

- [JavaScript Pure Functions](https://www.youtube.com/watch?v=BceIT1Lke-E)
- [What are Pure Functions?](https://www.youtube.com/watch?v=ZXxahQS1PN8)
