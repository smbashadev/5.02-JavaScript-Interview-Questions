# Asynchronous JavaScript Interview Questions (61–80)

This document contains the most frequently asked **JavaScript Asynchronous Programming Interview Questions**. The answers are written in simple, beginner-friendly language to help students, freshers, and developers prepare confidently for technical interviews.

---

# Q61. What is asynchronous programming?

## Answer

**Asynchronous programming** is a programming technique in which multiple tasks can be performed without waiting for one task to finish before starting another.

In JavaScript, asynchronous programming allows long-running tasks such as API calls, file operations, and timers to run in the background while the remaining code continues to execute.

This helps create faster and more responsive applications.

### Example

```javascript
console.log("Start");

setTimeout(function () {

    console.log("Task Completed");

}, 2000);

console.log("End");
```

### Output

```text
Start
End
Task Completed
```

### Explanation

- `"Start"` is printed first.
- `setTimeout()` schedules the callback to execute after 2 seconds.
- JavaScript continues executing the next statement without waiting.
- `"End"` is printed immediately.
- After 2 seconds, `"Task Completed"` is displayed.

### Key Points

- Executes long-running tasks in the background.
- Prevents blocking of the main thread.
- Improves application responsiveness.
- Commonly used with API calls, timers, and file operations.

### Interview Tip

JavaScript is **single-threaded**, but it can perform asynchronous operations using the Event Loop and Web APIs.

---

# Q62. What is the event loop?

## Answer

The **Event Loop** is a mechanism in JavaScript that continuously checks whether the **Call Stack** is empty.

If the Call Stack is empty, it moves ready callback functions from the **Callback Queue** (or Microtask Queue) to the Call Stack for execution.

The Event Loop enables JavaScript to perform asynchronous programming while remaining single-threaded.

### Execution Flow

```text
Call Stack
      ↓
Event Loop
      ↓
Callback Queue
```

### Example

```javascript
console.log("A");

setTimeout(function () {

    console.log("B");

}, 0);

console.log("C");
```

### Output

```text
A
C
B
```

### Explanation

- `"A"` is executed first.
- `setTimeout()` registers its callback with the Web API.
- `"C"` executes immediately.
- After the Call Stack becomes empty, the Event Loop moves the callback to the Call Stack.
- `"B"` is printed last.

### Key Points

- Continuously monitors the Call Stack.
- Moves callbacks to the Call Stack when it becomes empty.
- Works together with Web APIs and Callback Queue.
- Makes asynchronous programming possible.

### Interview Tip

Remember:

**The Event Loop never executes code directly. It only moves ready tasks to the Call Stack.**

---

# Q63. What is the call stack?

## Answer

The **Call Stack** is a data structure used by JavaScript to keep track of function execution.

Whenever a function is called, it is pushed onto the stack.

After the function finishes execution, it is removed (popped) from the stack.

The Call Stack follows the **LIFO (Last In, First Out)** principle.

### Example

```javascript
function first() {

    second();

}

function second() {

    console.log("Inside Second");

}

first();
```

### Output

```text
Inside Second
```

### Execution Order

```text
Call first()

↓

Push first()

↓

Call second()

↓

Push second()

↓

Execute second()

↓

Pop second()

↓

Pop first()
```

### Key Points

- Stores function calls.
- Follows the LIFO principle.
- Executes one function at a time.
- An infinite recursion can cause a Stack Overflow error.

### Interview Tip

The Call Stack is responsible for synchronous code execution in JavaScript.

---

# Q64. What is the callback queue?

## Answer

The **Callback Queue** (also called the Task Queue or Macrotask Queue) stores callback functions that are ready to execute after asynchronous operations are completed.

The Event Loop checks the Callback Queue and moves callbacks to the Call Stack when the Call Stack becomes empty.

### Example

```javascript
console.log("Start");

setTimeout(function () {

    console.log("Callback Executed");

}, 1000);

console.log("End");
```

### Output

```text
Start
End
Callback Executed
```

### Explanation

- `setTimeout()` registers its callback with the Web API.
- After the timer expires, the callback enters the Callback Queue.
- The Event Loop waits until the Call Stack is empty.
- The callback is then moved to the Call Stack and executed.

### Key Points

- Stores completed asynchronous callbacks.
- Works together with the Event Loop.
- Callbacks execute only when the Call Stack is empty.
- Essential for non-blocking JavaScript execution.

### Interview Tip

Do not confuse the **Callback Queue** with the **Call Stack**.

- **Call Stack** → Executes functions.
- **Callback Queue** → Stores completed asynchronous callbacks waiting for execution.

---

# Q65. What are Promises?

## Answer

A **Promise** is a JavaScript object that represents the eventual completion or failure of an asynchronous operation.

A Promise allows you to write asynchronous code in a cleaner and more organized way compared to nested callbacks.

### Syntax

```javascript
const promise = new Promise(function(resolve, reject) {

    // Asynchronous operation

});
```

### Example

```javascript
const promise = new Promise(function(resolve, reject) {

    let success = true;

    if (success) {

        resolve("Operation Successful");

    } else {

        reject("Operation Failed");

    }

});

promise
    .then(function(result) {

        console.log(result);

    })
    .catch(function(error) {

        console.log(error);

    });
```

### Output

```text
Operation Successful
```

### Explanation

- `resolve()` is called when the operation succeeds.
- `reject()` is called when the operation fails.
- `.then()` handles successful results.
- `.catch()` handles errors.

### Key Points

- Represents an asynchronous operation.
- Improves code readability.
- Helps avoid callback hell.
- Uses `.then()`, `.catch()`, and `.finally()`.

### Interview Tip

A Promise represents a value that may be available **now, later, or never**, making it one of the most important concepts in modern JavaScript.

---

---

# Q66. What are the states of a Promise?

## Answer

A Promise has **three possible states** that describe its current status during an asynchronous operation.

1. **Pending**
2. **Fulfilled (Resolved)**
3. **Rejected**

### Promise States

| State | Description |
|--------|-------------|
| Pending | The asynchronous operation is still in progress. |
| Fulfilled | The operation completed successfully. |
| Rejected | The operation failed due to an error. |

### Example

```javascript
const promise = new Promise(function(resolve, reject) {

    let success = true;

    if (success) {

        resolve("Data Loaded");

    } else {

        reject("Error Loading Data");

    }

});

promise
    .then(function(result) {

        console.log(result);

    })
    .catch(function(error) {

        console.log(error);

    });
```

### Output

```text
Data Loaded
```

### Explanation

- Initially, the Promise is in the **Pending** state.
- When `resolve()` is called, it becomes **Fulfilled**.
- If `reject()` is called, it becomes **Rejected**.

### Key Points

- Every Promise starts in the Pending state.
- A Promise can be settled only once.
- A settled Promise cannot change its state.
- Success is handled using `.then()`.
- Errors are handled using `.catch()`.

### Interview Tip

Remember the Promise lifecycle:

**Pending → Fulfilled** or **Pending → Rejected**

A Promise never moves back to the Pending state.

---

# Q67. What is `async/await`?

## Answer

`async` and `await` are ES2017 features that make asynchronous code easier to read and write.

They provide a cleaner alternative to chaining multiple `.then()` methods.

- `async` makes a function return a Promise.
- `await` pauses execution until the Promise is resolved.

### Syntax

```javascript
async function functionName() {

    const result = await promise;

}
```

### Example

```javascript
function getMessage() {

    return Promise.resolve("Hello JavaScript");

}

async function displayMessage() {

    const result = await getMessage();

    console.log(result);

}

displayMessage();
```

### Output

```text
Hello JavaScript
```

### Explanation

- `getMessage()` returns a Promise.
- `await` waits until the Promise is resolved.
- The resolved value is stored in `result`.

### Key Points

- Introduced in ES2017.
- Makes asynchronous code easier to understand.
- Reduces Promise chaining.
- Can only use `await` inside an `async` function.

### Interview Tip

Think of `async/await` as writing asynchronous code that looks and behaves like synchronous code.

---

# Q68. What is `Promise.all()`?

## Answer

`Promise.all()` executes multiple Promises simultaneously and waits until **all Promises are fulfilled**.

If any Promise is rejected, the entire `Promise.all()` is rejected immediately.

### Syntax

```javascript
Promise.all([promise1, promise2, promise3]);
```

### Example

```javascript
const promise1 = Promise.resolve("Java");

const promise2 = Promise.resolve("JavaScript");

const promise3 = Promise.resolve("SQL");

Promise.all([promise1, promise2, promise3])
.then(function(result) {

    console.log(result);

});
```

### Output

```text
["Java", "JavaScript", "SQL"]
```

### Explanation

- All Promises execute together.
- `Promise.all()` waits until every Promise completes successfully.
- The results are returned as an array.

### Key Points

- Executes multiple Promises concurrently.
- Returns an array of resolved values.
- Rejects immediately if one Promise fails.
- Improves performance when tasks are independent.

### Interview Tip

Use `Promise.all()` when **every asynchronous task must complete successfully** before continuing.

---

# Q69. What is `Promise.race()`?

## Answer

`Promise.race()` executes multiple Promises simultaneously and returns the result of the **first Promise that settles**, whether it is fulfilled or rejected.

The remaining Promises continue executing, but their results are ignored.

### Syntax

```javascript
Promise.race([promise1, promise2]);
```

### Example

```javascript
const promise1 = new Promise(resolve =>

    setTimeout(() => resolve("First"), 1000)

);

const promise2 = new Promise(resolve =>

    setTimeout(() => resolve("Second"), 2000)

);

Promise.race([promise1, promise2])
.then(function(result) {

    console.log(result);

});
```

### Output

```text
First
```

### Explanation

- Both Promises start at the same time.
- `promise1` finishes first.
- `Promise.race()` returns the result of the first completed Promise.

### Key Points

- Returns the first settled Promise.
- Ignores later Promise results.
- Can resolve or reject.
- Useful for implementing request timeouts.

### Interview Tip

Remember:

- `Promise.all()` → Waits for **all** Promises.
- `Promise.race()` → Returns the **first completed** Promise.

---

# Q70. What is `Promise.allSettled()`?

## Answer

`Promise.allSettled()` waits until **all Promises have completed**, regardless of whether they are fulfilled or rejected.

Unlike `Promise.all()`, it never fails because one Promise is rejected.

### Syntax

```javascript
Promise.allSettled([promise1, promise2]);
```

### Example

```javascript
const promise1 = Promise.resolve("Success");

const promise2 = Promise.reject("Failed");

Promise.allSettled([promise1, promise2])
.then(function(result) {

    console.log(result);

});
```

### Output

```text
[
  { status: "fulfilled", value: "Success" },
  { status: "rejected", reason: "Failed" }
]
```

### Explanation

- Every Promise is allowed to complete.
- The result contains the status of each Promise.
- No Promise prevents the others from finishing.

### Key Points

- Waits for all Promises.
- Returns the status of every Promise.
- Handles both fulfilled and rejected Promises.
- Useful when every result is important.

### Interview Tip

Remember the difference:

- `Promise.all()` → Fails if one Promise fails.
- `Promise.allSettled()` → Waits for every Promise and reports all results.

---

---

# Q71. What is `fetch()`?

## Answer

`fetch()` is a modern JavaScript method used to make **HTTP requests** to servers.

It returns a **Promise**, making it easy to work with asynchronous operations using `.then()` or `async/await`.

`fetch()` is commonly used to retrieve data from APIs.

### Syntax

```javascript
fetch(url)
    .then(function(response) {

        return response.json();

    })
    .then(function(data) {

        console.log(data);

    });
```

### Example

```javascript
fetch("https://jsonplaceholder.typicode.com/users/1")
.then(function(response) {

    return response.json();

})
.then(function(data) {

    console.log(data.name);

});
```

### Output

```text
Leanne Graham
```

### Explanation

- `fetch()` sends an HTTP request.
- The server returns a response.
- `response.json()` converts the response into a JavaScript object.
- The retrieved data is then displayed.

### Key Points

- Introduced as a modern replacement for AJAX using `XMLHttpRequest`.
- Returns a Promise.
- Supports `GET`, `POST`, `PUT`, `DELETE`, and other HTTP methods.
- Works well with `async/await`.

### Interview Tip

Remember that **`fetch()` does not automatically reject a Promise for HTTP errors like 404 or 500**. You should check `response.ok` before processing the response.

---

# Q72. What is AJAX?

## Answer

**AJAX (Asynchronous JavaScript and XML)** is a technique used to exchange data between a web browser and a server **without reloading the entire web page**.

Although AJAX originally used XML, modern applications mostly use JSON.

### Example

```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1")
.then(function(response) {

    return response.json();

})
.then(function(data) {

    console.log(data);

});
```

### Output

```text
{
  userId: 1,
  id: 1,
  title: "...",
  body: "..."
}
```

### Advantages of AJAX

- Updates web pages without refreshing.
- Improves user experience.
- Reduces server load.
- Makes web applications faster.

### Key Points

- Stands for Asynchronous JavaScript and XML.
- Enables background communication with servers.
- Commonly uses JSON instead of XML.
- Widely used in modern web applications.

### Interview Tip

Even though AJAX stands for **Asynchronous JavaScript and XML**, modern applications usually exchange data in **JSON** format.

---

# Q73. What are Web APIs?

## Answer

**Web APIs** are browser-provided features that allow JavaScript to perform tasks that are not part of the JavaScript language itself.

They enable JavaScript to interact with the browser and external resources.

Common Web APIs include:

- DOM API
- Fetch API
- Geolocation API
- Local Storage API
- Timer APIs (`setTimeout()` and `setInterval()`)

### Example

```javascript
setTimeout(function() {

    console.log("Executed");

}, 1000);
```

### Output

```text
Executed
```

### Explanation

`setTimeout()` is provided by the browser as a Web API.

JavaScript sends the timer request to the browser, which executes the callback after the specified delay.

### Key Points

- Provided by the browser.
- Not part of the JavaScript language.
- Enable asynchronous operations.
- Work together with the Event Loop.

### Interview Tip

Remember:

JavaScript itself does **not** provide `fetch()` or `setTimeout()`.

These are **Web APIs** provided by the browser.

---

# Q74. What is `setTimeout()`?

## Answer

`setTimeout()` is a JavaScript timer function that executes a callback function **once** after a specified delay.

### Syntax

```javascript
setTimeout(function() {

    // Code

}, delayInMilliseconds);
```

### Example

```javascript
console.log("Start");

setTimeout(function() {

    console.log("Executed After 2 Seconds");

}, 2000);

console.log("End");
```

### Output

```text
Start
End
Executed After 2 Seconds
```

### Explanation

- The callback is registered with the browser.
- JavaScript continues executing the remaining code.
- After the specified delay, the callback is placed in the Callback Queue.
- The Event Loop executes it when the Call Stack is empty.

### Key Points

- Executes only once.
- Delay is measured in milliseconds.
- Asynchronous in nature.
- Frequently used for delayed execution.

### Interview Tip

A delay of `0` milliseconds **does not mean immediate execution**.

The callback executes only after the Call Stack becomes empty.

---

# Q75. What is `setInterval()`?

## Answer

`setInterval()` repeatedly executes a callback function at a specified time interval until it is stopped.

### Syntax

```javascript
setInterval(function() {

    // Code

}, intervalInMilliseconds);
```

### Example

```javascript
let count = 1;

const timer = setInterval(function() {

    console.log("Count:", count);

    count++;

    if (count > 3) {

        clearInterval(timer);

    }

}, 1000);
```

### Output

```text
Count: 1
Count: 2
Count: 3
```

### Explanation

- The callback executes every second.
- `clearInterval()` stops the repeated execution after the count reaches `3`.

### Key Points

- Executes repeatedly.
- Uses milliseconds for the interval.
- Continues until stopped.
- Commonly used for clocks, timers, and animations.

### Interview Tip

Remember the difference:

- `setTimeout()` → Executes once.
- `setInterval()` → Executes repeatedly until cleared.

---

---

# Q76. What is `clearTimeout()`?

## Answer

`clearTimeout()` is a JavaScript method used to cancel a timer that was created using `setTimeout()` before it executes.

When `clearTimeout()` is called with the timer ID returned by `setTimeout()`, the scheduled callback function will not be executed.

### Syntax

```javascript
const timerId = setTimeout(function() {

    // Code

}, delay);

clearTimeout(timerId);
```

### Example

```javascript
const timer = setTimeout(function() {

    console.log("This message will not appear.");

}, 3000);

clearTimeout(timer);

console.log("Timer Cancelled");
```

### Output

```text
Timer Cancelled
```

### Explanation

- `setTimeout()` schedules a callback.
- The timer ID is stored in the `timer` variable.
- `clearTimeout(timer)` cancels the scheduled callback before execution.

### Key Points

- Cancels a pending `setTimeout()`.
- Prevents delayed execution.
- Requires the timer ID returned by `setTimeout()`.
- Useful for cancelling unnecessary tasks.

### Interview Tip

Always store the return value of `setTimeout()` if you may need to cancel the timer later using `clearTimeout()`.

---

# Q77. What is `clearInterval()`?

## Answer

`clearInterval()` is a JavaScript method used to stop a repeating timer created using `setInterval()`.

It prevents the callback function from executing repeatedly after it is called.

### Syntax

```javascript
const intervalId = setInterval(function() {

    // Code

}, interval);

clearInterval(intervalId);
```

### Example

```javascript
let count = 1;

const timer = setInterval(function() {

    console.log(count);

    count++;

    if (count > 3) {

        clearInterval(timer);

    }

}, 1000);
```

### Output

```text
1
2
3
```

### Explanation

- `setInterval()` repeatedly executes the callback.
- After printing `3`, `clearInterval()` stops further execution.
- No additional output is produced.

### Key Points

- Stops a repeating timer.
- Requires the timer ID returned by `setInterval()`.
- Helps avoid unnecessary resource usage.
- Commonly used in timers, clocks, animations, and games.

### Interview Tip

Remember:

- `clearTimeout()` → Stops a delayed task.
- `clearInterval()` → Stops a repeating task.

---

# Q78. What is callback hell?

## Answer

**Callback Hell** is a situation where multiple callback functions are nested inside one another, making the code difficult to read, understand, and maintain.

This often happens when performing several asynchronous operations in sequence.

### Example

```javascript
loginUser(function(user) {

    getOrders(user, function(orders) {

        getPayment(orders, function(payment) {

            console.log(payment);

        });

    });

});
```

### Explanation

- Each asynchronous task depends on the previous one.
- Callbacks become deeply nested.
- The code becomes harder to debug and maintain.

### Key Points

- Results in deeply nested callbacks.
- Reduces code readability.
- Makes debugging more difficult.
- Common in older asynchronous JavaScript code.

### Interview Tip

Callback Hell is sometimes called the **"Pyramid of Doom"** because the nested code forms a pyramid-like structure.

---

# Q79. How do you avoid callback hell?

## Answer

Callback Hell can be avoided by using modern JavaScript features that simplify asynchronous programming.

The most common approaches are:

- Promises
- `async/await`
- Modular functions
- Proper error handling

### Example Using Promises

```javascript
loginUser()
.then(getOrders)
.then(getPayment)
.then(function(payment) {

    console.log(payment);

})
.catch(function(error) {

    console.log(error);

});
```

### Example Using `async/await`

```javascript
async function processUser() {

    try {

        const user = await loginUser();

        const orders = await getOrders(user);

        const payment = await getPayment(orders);

        console.log(payment);

    } catch (error) {

        console.log(error);

    }

}
```

### Key Points

- Prefer Promises instead of nested callbacks.
- Use `async/await` for better readability.
- Split large functions into smaller reusable functions.
- Handle errors using `catch()` or `try...catch`.

### Interview Tip

Today, most JavaScript applications use **Promises** and **async/await** instead of nested callbacks because they make asynchronous code cleaner and easier to maintain.

---

# Q80. What are microtasks and macrotasks?

## Answer

JavaScript uses **Microtask Queue** and **Macrotask Queue** to manage asynchronous operations.

The Event Loop always processes **all Microtasks before processing the next Macrotask**.

### Common Microtasks

- Promise callbacks (`.then()`, `.catch()`, `.finally()`)
- `queueMicrotask()`
- `MutationObserver`

### Common Macrotasks

- `setTimeout()`
- `setInterval()`
- DOM Events
- I/O Operations

### Example

```javascript
console.log("Start");

setTimeout(function() {

    console.log("Macrotask");

}, 0);

Promise.resolve().then(function() {

    console.log("Microtask");

});

console.log("End");
```

### Output

```text
Start
End
Microtask
Macrotask
```

### Explanation

- `"Start"` and `"End"` execute first.
- Promise callbacks are placed in the **Microtask Queue**.
- `setTimeout()` callbacks are placed in the **Macrotask Queue**.
- The Event Loop processes all Microtasks before executing the next Macrotask.

### Key Points

- Microtasks have higher priority than Macrotasks.
- Promise callbacks are Microtasks.
- Timer callbacks are Macrotasks.
- The Event Loop executes all pending Microtasks before the next Macrotask.

### Interview Tip

One of the most frequently asked JavaScript interview questions is:

**Which executes first: a Promise callback or `setTimeout()`?**

Answer:

**Promise callbacks execute first because they are Microtasks, while `setTimeout()` callbacks are Macrotasks.**

---
