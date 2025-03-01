**Hoisting** is a JavaScript behavior where **variable and function declarations** are moved (or "hoisted") to the top of their containing scope **during the compile phase**, 
before the code has been executed. 
This means that you can reference variables and functions before they are actually declared in the code.

However, **only declarations** are hoisted, **not initializations** (assignments).

Let's break it down with examples:

### 1. **Hoisting with Variables**

Example 1: `var`
```javascript
console.log(x); // undefined
var x = 5;
console.log(x); // 5
```
- **Explanation**: The declaration `var x;` is hoisted to the top, but the initialization (`x = 5`) happens at the line where it's written.
- This results in `undefined` being printed first because `x` is declared but not yet assigned a value at the time of the first `console.log`.

#### Example 2: `let` and `const`
```javascript
console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 10;
```
- **Explanation**: `let` and `const` are **not** hoisted in the same way as `var`. They enter a **temporal dead zone (TDZ)** from the start of the block until the variable is initialized, meaning you can't access them before their declaration line.

### 2. **Hoisting with Functions**

Example 3: Function Declarations
```javascript
hello(); // "Hello, World!"

function hello() {
  console.log("Hello, World!");
}
```
- **Explanation**: Function declarations are hoisted with both the declaration and definition. That's why you can call `hello()` before it appears in the code.

#### Example 4: Function Expressions and Arrow function as well
```javascript
myFunc(); // TypeError: myFunc is not a function

var myFunc = function() {
  console.log("Hello!");
};
```
- **Explanation**: Here, only the variable `myFunc` is hoisted (with `undefined` as its initial value), not the function assignment. So, when trying to call `myFunc()` before its assignment, JavaScript sees `myFunc` as `undefined`, which causes a TypeError.

### Key Takeaways:
- **Variables declared with `var`** are hoisted and initialized with `undefined`.
- **Variables declared with `let` and `const`** are hoisted but are not accessible until they are initialized (this is the Temporal Dead Zone).
- **Function declarations** are hoisted with their definitions, so you can call them before they're written in the code.
- **Function expressions** (whether using `var`, `let`, or `const`) are hoisted, but only the variable declaration is hoisted, not the assignment.
