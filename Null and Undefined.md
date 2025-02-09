
```markdown
### 3. What is the difference between `null` and `undefined`?

The difference between `null` and `undefined` in JavaScript lies in their meaning and usage:

#### 1. `undefined`:
- Meaning: It represents a variable that has been declared but has not yet been assigned a value. 
  It’s the default value assigned to variables that are declared but not initialized.

- Type: `undefined` is its own type in JavaScript (`typeof undefined` is `"undefined"`).
- Use cases: It’s often used to indicate that a value is missing, uninitialized, or unknown. For example:
  ```javascript
  let a;
  console.log(a); // undefined (variable is declared but not initialized)
  ```

#### 2. `null`:
- **Meaning**: It represents the intentional absence of any value or object. It is explicitly assigned to a variable to indicate that it should not have a value.
- **Type**: `null` is of type `object` (which is a known JavaScript quirk). (`typeof null` returns `"object"`, but it's a primitive value).
- **Use cases**: It is typically used to indicate that a variable should hold an object, but it currently does not.
  ```javascript
  let b = null;
  console.log(b); // null (explicitly assigned to indicate no value)
  ```

### Summary:
- `undefined` means a variable is declared but has no value assigned.
- `null` is an intentional assignment to indicate no value or object.

Both `null` and `undefined` are "falsy" values, but they differ in terms of meaning and usage in the code.
```
