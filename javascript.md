

# JavaScript Technical Reference

## 1. Different Data Types in JavaScript

JavaScript has **7 primitive data types** and **1 non-primitive type**:

### Primitive Types:

1. **Number** – `let age = 25;`
2. **String** – `let name = "Akshitha";`
3. **Boolean** – `let isStudent = true;`
4. **Null** – `let data = null;` (intentional absence of value)
5. **Undefined** – `let value;` (declared but not assigned)
6. **Symbol** – `let sym = Symbol("id");`
7. **BigInt** – `let big = 1234567890123456789012345678901234567890n;`

### Non-Primitive Type:

* **Object** – `let person = {name: "Akshitha", age: 28};`

---

## 2. `let`, `var`, `const`

| Keyword | Scope           | Hoisting                 | Reassignable |
| ------- | --------------- | ------------------------ | ------------ |
| `var`   | Function-scoped | Yes (undefined)          | Yes          |
| `let`   | Block-scoped    | Yes (temporal dead zone) | Yes          |
| `const` | Block-scoped    | Yes (temporal dead zone) | No           |

### Why we must not use `var`:

* `var` is function-scoped, which can cause unexpected behavior in loops or blocks.
* It is hoisted and initialized as `undefined`, which may lead to bugs.

---

## 3. Global Variables

* Declaring variables globally can **pollute the global scope** and cause naming conflicts.
* Example:

```js
var a = 10; // global
function test() {
  console.log(a); // can accidentally access global `a`
}
```

---

## 4. Truthy and Falsy Values

### Falsy Values:

`false`, `0`, `""`, `null`, `undefined`, `NaN`

### Truthy Values:

All values that are not falsy, including objects, arrays, and non-empty strings.

---

## 5. Function Hoisting

* **Function declarations** are hoisted.

```js
sayHello();
function sayHello() {
  console.log("Hello!");
}
```

* **Function expressions** are **not hoisted**:

```js
sayHi(); // Error
const sayHi = function() { console.log("Hi!"); }
```

---

## 6. Function Without Return Statement

* Returns `undefined` by default.

```js
function add(a, b) { let sum = a + b; }
console.log(add(2, 3)); // undefined
```

---

## 7. Different Ways to Declare a Function

1. **Function Declaration**

```js
function add(a, b) { return a + b; }
```

2. **Function Expression**

```js
const add = function(a, b) { return a + b; }
```

3. **Arrow Function**

```js
const add = (a, b) => a + b;
```

---

## 8. Pass by Value and Pass by Reference

* **Primitive Types** → pass by value
* **Objects/Arrays** → pass by reference

```js
let x = 10;
let y = x; // copy value
y = 20; 
console.log(x); // 10

let obj1 = {name: "Akshitha"};
let obj2 = obj1; // reference
obj2.name = "Aravind";
console.log(obj1.name); // Aravind
```

---

## 9. Different Types of Loops

### For with Numbers

```js
for(let i=0; i<5; i++){ console.log(i); }
```

### For..in (object keys)

```js
const person = {name: "A", age: 20};
for(let key in person){ console.log(key, person[key]); }
```

### For..of (iterable values)

```js
const arr = [1,2,3];
for(let value of arr){ console.log(value); }
```

### forEach

```js
arr.forEach(val => console.log(val));
```

---

## 10. Searching MDN

* Use **MDN Web Docs**: [https://developer.mozilla.org](https://developer.mozilla.org)
* Search for keywords like `Array.map`, `Promise`, `String methods`.

---

## 11. Popular Array Utility Methods

* `map`, `filter`, `reduce`, `find`, `some`, `every`, `includes`, `indexOf`, `push`, `pop`, `shift`, `unshift`, `slice`, `splice`, `sort`, `reverse`

---

## 12. Popular String Utility Methods

* `length`, `includes`, `indexOf`, `slice`, `substring`, `replace`, `toLowerCase`, `toUpperCase`, `trim`, `split`, `charAt`

---

## 13. Popular Object Utility Methods

* `Object.keys()`, `Object.values()`, `Object.entries()`, `Object.assign()`, `Object.freeze()`, `Object.seal()`, `hasOwnProperty()`

---

## 14. forEach vs map/filter/reduce

* **forEach**: use when you need **side effects** (no return value)
* **map/filter/reduce**: use for **returning new arrays or single value**

---

## 15. Immutable and Mutable Methods

* **Mutable methods**: modify original array → `push`, `pop`, `splice`, `sort`, `reverse`
* **Immutable methods**: return new array → `map`, `filter`, `slice`, `concat`

---

## 16. Error Handling

### try-catch

```js
try {
  throw new Error("Something went wrong");
} catch(error) {
  console.error(error.message);
} finally {
  console.log("Always executes");
}
```

### Throwing errors

* `throw new Error("Error message");` → Error object with stack trace
* `throw "Error message";` → throws string (less useful)

### Importance of catch

* Prevents program from crashing
* Handles runtime errors gracefully

---

## 17. Spread Operator

```js
let arr1 = [1,2];
let arr2 = [...arr1, 3, 4];
console.log(arr2); // [1,2,3,4]
```

---

## 18. Template Literals

```js
let name = "Akshitha";
let msg = `Hello ${name}, welcome!`;
```

---

## 19. Default Parameters

```js
function greet(name="Guest"){ console.log(`Hello ${name}`); }
greet(); // Hello Guest
```

---

## 20. Destructuring

### Array

```js
let [a,b] = [1,2];
```

### Object

```js
let {name, age} = {name:"A", age:20};
```

---

## 21. Closures

* A function that **remembers its outer scope** even after the outer function executes

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
```

---

## 22. Arrow Functions vs Regular Functions

| Feature            | Regular   | Arrow         |
| ------------------ | --------- | ------------- |
| `this` binding     | Dynamic   | Lexical       |
| `arguments` object | Available | Not available |
| Can be constructor | Yes       | No            |

---

## 23. `===` vs `==`

* `==` → checks value only (type coercion)
* `===` → checks value and type (strict equality)

```js
0 == "0" // true
0 === "0" // false
```

---

## 24. `value === undefined` vs `!value`

* `!value` is **truthy/falsy check**, can be misleading
* `value === undefined` is **explicit check for undefined**

---

## 25. Array Utility Methods Chaining

```js
let arr = [1,2,3,4];
let result = arr.filter(x=>x%2==0).map(x=>x*2).reduce((a,b)=>a+b,0);
console.log(result); // 12
```

---

## 26. `null` vs `undefined`

| Feature | null     | undefined          |
| ------- | -------- | ------------------ |
| Type    | object   | undefined          |
| Meaning | no value | value not assigned |

---

## 27. Modules (Node.js)

### Exporting

```js
// module.js
const add = (a,b)=>a+b;
module.exports = add;
```

### Importing

```js
const add = require("./module");
console.log(add(2,3));
```

---

## 28. Console Methods

* `console.log()`, `console.error()`, `console.warn()`, `console.info()`, `console.table()`, `console.time()`, `console.timeEnd()`

---

## 29. Best Practices

* Proper indentation
* Meaningful variable names
* Loop variable names should be descriptive
* Avoid global variables
* Use `const` for constants

---

## 30. Higher Order Functions

* Passing function as an argument

```js
function greet(fn){
  fn();
}
function sayHello(){ console.log("Hello"); }
greet(sayHello); // Hello
```

---

## 31. Named vs Anonymous Functions

* Named function: `function add(a,b){}`
* Anonymous function: `const add = function(a,b){}`

---

## 32. Variable Number of Arguments

```js
function sum(...nums){
  return nums.reduce((a,b)=>a+b,0);
}
console.log(sum(1,2,3,4)); // 10
```

---

