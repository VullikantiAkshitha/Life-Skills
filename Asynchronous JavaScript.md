
# Asynchronous JavaScript & Promises – Technical Guide

## 1. How JavaScript Executes Code
- JavaScript is **single-threaded**, meaning it executes one task at a time.  
- It uses a **call stack** to keep track of function execution.  
- Synchronous code is executed line by line.  
- Asynchronous code allows certain tasks to be executed in the background while the main thread continues.

---

## 2. Synchronous vs Asynchronous

| Synchronous | Asynchronous |
|------------|--------------|
| Executes line by line | Executes tasks without blocking main thread |
| Each task waits for previous task to complete | Tasks can run in the background |
| Example: `console.log()` | Example: `setTimeout`, AJAX requests |

---

## 3. Ways to Make JavaScript Async
- **Callbacks** (function passed as argument)
- **Promises**
- **Async/Await**
- Browser APIs (`fetch`, `setTimeout`, `setInterval`)

---

## 4. Web Browser APIs
- These are APIs provided by the browser to perform tasks **outside the main JS thread**, such as:
  - Timers: `setTimeout`, `setInterval`
  - Network requests: `fetch`, `XMLHttpRequest`
  - DOM events
- They allow asynchronous operations to happen while JS continues execution.

---

## 5. Event Loop
- The **event loop** continuously checks:
  1. **Call stack** – is it empty?
  2. **Task queue / Callback queue** – are there pending callbacks?
- If the call stack is empty, tasks from the queue are moved to the call stack.
- This is how asynchronous callbacks are executed after their task is done.

---

## 6. Callbacks

### What is a Callback Hell?
- Nested callbacks causing code to become unreadable and hard to maintain.  
```js
doSomething(function(result1){
  doSomethingElse(result1, function(result2){
    doAnotherThing(result2, function(result3){
      // and so on...
    });
  });
});
````

### Inversion of Control in Callbacks

* The **control of function execution is handed over** to another function.
* The function does not decide when to execute the callback; the async operation does.

---

## 7. Promises

### What is a Promise?

* A Promise is an object representing the **eventual completion or failure** of an asynchronous operation.

### Creating a Promise

```js
const myPromise = new Promise((resolve, reject) => {
  // async task
  if(success) resolve(value);
  else reject(error);
});
```

### States of a Promise

* **Pending** – initial state, neither fulfilled nor rejected
* **Fulfilled** – operation completed successfully
* **Rejected** – operation failed

### Consuming a Promise

```js
myPromise.then(value => {
  console.log(value);
}).catch(error => {
  console.error(error);
});
```

---

## 8. Promise Chaining

### Chaining using `.then()`

```js
fetchData()
  .then(data => processData(data))
  .then(result => console.log(result))
  .catch(err => console.error(err));
```

### Error Handling in a Promise Chain

* `.catch()` catches any error thrown in previous `.then()`
* `.finally()` executes regardless of outcome

### Behavior

* **Error inside `.then` with `.catch` present** → `.catch` handles it
* **Error inside `.then` with no `.catch`** → Unhandled Promise Rejection
* **Always place `.catch` at the end** to catch errors from entire chain

---

## 9. Consuming Multiple Promises

### Using `.then` chaining

```js
promise1()
  .then(result1 => promise2())
  .then(result2 => promise3())
  .catch(err => console.error(err));
```

### Using `Promise.all()`

```js
Promise.all([promise1(), promise2(), promise3()])
  .then(results => console.log(results))
  .catch(err => console.error(err));
```

* Waits for **all promises to resolve**
* Rejects immediately if any promise fails

### Other Promise Utilities

* `Promise.resolve(value)` – returns a resolved promise
* `Promise.reject(error)` – returns a rejected promise
* `Promise.allSettled([promises])` – waits for all promises, returns their status
* `Promise.any([promises])` – resolves as soon as any promise resolves
* `Promise.race([promises])` – resolves/rejects as soon as first promise resolves/rejects

---

## 10. Promisifying Async Callbacks

Example: `setTimeout`

```js
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

delay(1000).then(() => console.log("1 second passed"));
```

---

## 11. Importance of Error Handling

* Errors in asynchronous code are **not caught by try/catch** outside
* Promises allow structured error handling with `.catch()`
* Proper error handling prevents unhandled rejections and application crashes

---

## References

* [MDN: Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
* [JavaScript Info: Event Loop](https://javascript.info/event-loop)
* [MDN: Async functions](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Promises)

```

---

