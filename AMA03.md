

---



## 1. Difference Between Synchronous and Asynchronous Code Execution

### **Synchronous Execution**
- JavaScript executes code **line by line** — each operation must complete before the next one starts.
- Blocking nature: if one line takes time (e.g., heavy computation), the rest of the code must **wait**.
  
**Example:**
```js
console.log("Task 1");
console.log("Task 2");
console.log("Task 3");
// Output: Task 1 → Task 2 → Task 3
````

### **Asynchronous Execution**

* Allows the program to **start a task**, continue running other code, and **handle the result later**.
* Non-blocking — uses **callbacks, promises, or async/await** to manage tasks.

**Example:**

```js
console.log("Task 1");
setTimeout(() => console.log("Task 2"), 2000);
console.log("Task 3");
// Output: Task 1 → Task 3 → Task 2
```

---

## 2. Event Loop in JavaScript

### **Definition**

The **Event Loop** is the mechanism that allows JavaScript to perform **non-blocking asynchronous operations** — even though it has a **single-threaded** runtime.

### **How it works**

1. All code runs inside a **Call Stack**.
2. **Web APIs** (like `setTimeout`, `fetch`) run asynchronously.
3. When async tasks complete, their callbacks are sent to the **Callback Queue**.
4. The **Event Loop** continuously checks:

   * If the **Call Stack** is empty → It moves callbacks from the **Queue** to the **Stack** for execution.

### **Simple Visualization**

```
Call Stack <—> Event Loop <—> Callback Queue
```

---

## 3. Callback Hell and Inversion of Control

### **Callback**

A callback is a function passed as an argument to another function and executed after some operation completes.

### **Callback Hell**

When multiple asynchronous callbacks are nested inside each other, code becomes:

* Hard to read,
* Difficult to maintain,
* Error-prone.

**Example:**

```js
getData(function(a) {
  processData(a, function(b) {
    saveData(b, function(c) {
      console.log("Done!");
    });
  });
});
```

This deep nesting is known as **Callback Hell**.

### **Inversion of Control**

When you pass a callback to another function, **you give control** of when and how that callback is executed to someone else.
If that function fails to call your callback or calls it incorrectly → your code breaks.

---

## 4. Three States of a Promise

A **Promise** represents the eventual completion (or failure) of an asynchronous operation.

| State         | Meaning                                    | Triggered By           |
| ------------- | ------------------------------------------ | ---------------------- |
| **Pending**   | Initial state; operation not completed yet | Before result is known |
| **Fulfilled** | Operation completed successfully           | `resolve()` called     |
| **Rejected**  | Operation failed                           | `reject()` called      |

**Example:**

```js
const promise = new Promise((resolve, reject) => {
  const success = true;
  success ? resolve("Done!") : reject("Error!");
});
```

---

## 5. Promise Chaining and Error Handling

### **Promise Chaining**

You can connect multiple `.then()` methods in sequence — each receiving the result of the previous one.

**Example:**

```js
fetchData()
  .then(data => processData(data))
  .then(result => saveData(result))
  .then(() => console.log("All done!"))
  .catch(err => console.error("Error:", err));
```

* Each `.then()` returns a **new promise**.
* `.catch()` handles any error in the entire chain.

### **Error Handling**

* Use `.catch()` at the end of a chain.
* Or handle locally by returning a new promise with recovery logic.

---

## 6. Difference Between `Promise.all`, `Promise.allSettled`, `Promise.any`, and `Promise.race`

| Method                 | Resolves When                                 | Rejects When             | Returns                                   |
| ---------------------- | --------------------------------------------- | ------------------------ | ----------------------------------------- |
| **Promise.all**        | All promises are fulfilled                    | Any one rejects          | Array of results                          |
| **Promise.allSettled** | All promises settle (fulfilled or rejected)   | Never rejects            | Array of objects `{status, value/reason}` |
| **Promise.any**        | First promise fulfills                        | All promises reject      | Value of first fulfilled                  |
| **Promise.race**       | First promise settles (fulfilled or rejected) | Depends on first settled | Value or error of the first settled       |


Would you like me to **add code output examples and diagrams** (like Event Loop illustration and Promise flow diagram) in the `.md` file to make it look more like a *presentation-ready technical report*?
```
