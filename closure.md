# Understanding Closures in JavaScript

### 1. **What is a Closure?**
A closure is a function that "remembers" its lexical scope (the environment in which it was created)
 even after the outer function has finished executing. 

In simple terms, a closure allows an inner function to access variables from an outer function
even after the outer function has completed.

---

### 2. Closure Example:

```
function createCounter() {
  let count = 0; // Outer function's variable

  // Inner function (closure)
  return function() {
    count++;  // Inner function modifies and accesses outer function's variable
    console.log(count);
  };
}

const counter = createCounter(); // createCounter() is executed
counter(); // Output: 1
counter(); // Output: 2
counter(); // Output: 3
