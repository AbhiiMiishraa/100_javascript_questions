
```markdown
# JavaScript Hoisting Explained

In JavaScript, hoisting applies to variable declarations and function declarations. 
However, the exact behavior depends on how the variable or function is declared 
(using `var`, `let`, `const`, or function declarations/expressions). 

Here’s a breakdown of what exactly gets hoisted:

## 1. Variable Declarations (`var`)
- What gets hoisted: Only the declaration of the variable (not the assignment).
- How it behaves: The declaration is moved to the top of the scope and is initialized with `undefined`.

#### Example:
```console.log(a); // undefined
var a = 10;
console.log(a); // 10
```
- **Explanation**: The declaration `var a;` is hoisted, but the initialization (`a = 10`) is not.

## 2. **Function Declarations**
- **What gets hoisted**: Both the **function declaration** and its **definition** (body).
- **How it behaves**: You can call the function before it's written in the code because the entire function (both name and code) is hoisted to the top.

#### Example:
```javascript
myFunction(); // "Hello, World!"

function myFunction() {
  console.log("Hello, World!");
}
```
- **Explanation**: The entire function declaration is hoisted, so calling `myFunction()` before its declaration works fine.

## 3. **`let` and `const` Declarations**
- **What gets hoisted**: The **declaration** is hoisted, but the **initialization** is not.
- **How it behaves**: They go into a **temporal dead zone (TDZ)** from the start of the block until the initialization, so you can't access them before they are assigned.

#### Example with `let`:
```javascript
console.log(x); // ReferenceError: Cannot access 'x' before initialization
let x = 20;
```
- **Explanation**: The `let` declaration is hoisted, but the initialization doesn’t happen until the line `let x = 20;`. During this time, accessing `x` results in a ReferenceError due to the Temporal Dead Zone.

#### Example with `const`:
```javascript
console.log(y); // ReferenceError: Cannot access 'y' before initialization
const y = 30;
```
- **Explanation**: Similar to `let`, the `const` declaration is hoisted, but you can't access `y` before it's initialized, leading to a ReferenceError.

## 4. **Function Expressions (Including Arrow Functions)**
- **What gets hoisted**: Only the **variable declaration** is hoisted (like with `var`), not the assignment of the function expression.
- **How it behaves**: If you try to call the function before the assignment, you’ll get an error.

#### Example with Function Expression:
```javascript
myFunc(); // TypeError: myFunc is not a function

var myFunc = function() {
  console.log("Hello!");
};
```
- **Explanation**: The declaration `var myFunc;` is hoisted, but the function assignment is not. At the time of the call, `myFunc` is `undefined`, which leads to a TypeError when trying to call it as a function.

#### Example with Arrow Function:
```javascript
myArrowFunc(); // TypeError: myArrowFunc is not a function

const myArrowFunc = () => {
  console.log("Hello!");
};
```
- **Explanation**: Similar to function expressions, the variable `myArrowFunc` is hoisted, but not the assignment of the arrow function.

## Key Points Summary:
1. **`var` declarations** are hoisted and initialized to `undefined`.
2. **`let` and `const` declarations** are hoisted but are in the **temporal dead zone** until initialized (cannot be accessed before initialization).
3. **Function declarations** are hoisted along with their body, meaning they can be invoked before the actual code appears.
4. **Function expressions** (including arrow functions) only hoist the **variable** declaration, not the function assignment, so they can't be called before the function is defined.

## What Is Not Hoisted:
- **Assignments**: Only the **declarations** of variables and functions are hoisted. The values or function definitions are not hoisted, so assignments happen at the line of code where they are written.
- **Class Declarations**: Classes are not hoisted like function declarations. They behave more like `let`/`const` in that they cannot be accessed before their declaration.
