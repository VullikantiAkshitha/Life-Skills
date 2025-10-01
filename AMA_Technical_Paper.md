

## 1. What is the difference between let, var, and const?
- **var**: Function-scoped, can be redeclared and updated. Hoisted with `undefined` initialization.
- **let**: Block-scoped, cannot be redeclared in the same scope but can be updated. Hoisted but not initialized (Temporal Dead Zone).
- **const**: Block-scoped, must be initialized during declaration, cannot be reassigned. However, objects and arrays declared with `const` can still be mutated.

---

## 2. Why is using global variables considered a bad practice?
- They can be accessed and modified from anywhere, which increases the chance of **accidental overwrites**.
- Harder to **debug and maintain**, since many parts of code may depend on them.
- Reduce **modularity** and reusability of code.
- In large applications, excessive globals can lead to **naming collisions**.

---

## 3. Explain pass by reference vs pass by value.
- **Pass by value**: A copy of the actual value is passed. Changes inside the function do not affect the original variable. (e.g., **primitive types** like `number`, `string`, `boolean`).
- **Pass by reference**: A reference (memory address) is passed, not a copy. Changes inside the function affect the original variable. (e.g., **objects, arrays, functions**).

---

## 4. What are the different types of for loops in JavaScript?
- **for loop**: Classic loop with initializer, condition, and increment (`for (let i = 0; i < n; i++)`).
- **for...in loop**: Iterates over **enumerable properties** of an object (keys).
- **for...of loop**: Iterates over **iterable objects** like arrays, strings, maps, sets (values).
- **forEach method**: Executes a function for each element of an array.

---

## 5. When should we use forEach, and when should we use array utility methods like map, filter, reduce?
- **forEach**: Used for performing **side effects** (e.g., logging, updating DOM). It doesn’t return a new array.
- **map**: Used when you want to **transform each element** and get a new array.
- **filter**: Used when you want to **select elements** based on a condition and return a new array.
- **reduce**: Used when you want to **accumulate values** into a single result (e.g., sum, average, object creation).

---

## 6. What is the difference between `throw new Error("msg")` and `throw "msg"`?
- `throw new Error("msg")`: Creates an **Error object** with stack trace, making debugging easier. Preferred way to throw errors.
- `throw "msg"`: Throws a **string literal** (or any value). Provides less debugging information since no stack trace is available.

---

## 7. What are closures in JavaScript?
- A **closure** is a function that "remembers" its lexical scope even when executed outside of that scope.
- Example:
  ```js
  function outer() {
    let count = 0;
    return function inner() {
      count++;
      return count;
    }
  }

  const counter = outer();
  console.log(counter()); // 1
  console.log(counter()); // 2
````
