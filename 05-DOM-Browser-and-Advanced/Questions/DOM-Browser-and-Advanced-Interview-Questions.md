# DOM, Browser & Advanced Concepts Interview Questions (81–100)

This document contains the most frequently asked **JavaScript DOM, Browser & Advanced Concepts Interview Questions**. The answers are written in simple, beginner-friendly language to help students, freshers, and developers prepare confidently for technical interviews.

---

# Q81. What is the DOM?

## Answer

The **DOM (Document Object Model)** is a programming interface provided by web browsers that represents an HTML or XML document as a tree of objects.

Using the DOM, JavaScript can access, modify, add, or remove HTML elements, attributes, and styles dynamically.

### Example

```html
<!DOCTYPE html>
<html>

<body>

<h1 id="title">Hello World</h1>

<script>

const heading = document.getElementById("title");

heading.textContent = "Welcome to JavaScript";

</script>

</body>

</html>
```

### Output

```text
Before:
Hello World

After:
Welcome to JavaScript
```

### Explanation

- The browser converts the HTML document into a DOM tree.
- JavaScript accesses the `<h1>` element using its `id`.
- The text content is updated dynamically without reloading the page.

### Key Points

- DOM stands for Document Object Model.
- Represents an HTML document as objects.
- Allows JavaScript to modify web pages dynamically.
- Created automatically by the browser.

### Interview Tip

The DOM is **not part of JavaScript**. It is a browser-provided API that JavaScript uses to interact with web pages.

---

# Q82. How do you select DOM elements?

## Answer

JavaScript provides several methods to select HTML elements from the DOM.

The most commonly used methods are:

- `getElementById()`
- `getElementsByClassName()`
- `getElementsByTagName()`
- `querySelector()`
- `querySelectorAll()`

### Example Using `getElementById()`

```javascript
const heading = document.getElementById("title");

console.log(heading);
```

### Example Using `querySelector()`

```javascript
const element = document.querySelector(".box");

console.log(element);
```

### Example Using `querySelectorAll()`

```javascript
const paragraphs = document.querySelectorAll("p");

console.log(paragraphs);
```

### Common DOM Selection Methods

| Method | Description |
|---------|-------------|
| `getElementById()` | Selects an element by its ID |
| `getElementsByClassName()` | Selects elements by class name |
| `getElementsByTagName()` | Selects elements by tag name |
| `querySelector()` | Selects the first matching element |
| `querySelectorAll()` | Selects all matching elements |

### Key Points

- Multiple methods are available for selecting elements.
- `querySelector()` returns the first matching element.
- `querySelectorAll()` returns all matching elements.
- DOM selection is the first step before manipulating elements.

### Interview Tip

Modern JavaScript applications commonly use **`querySelector()`** and **`querySelectorAll()`** because they support CSS selectors.

---

# Q83. What is event bubbling?

## Answer

**Event bubbling** is the default event propagation mechanism in JavaScript.

When an event occurs on a child element, it first executes on the target element and then propagates upward through its parent elements until it reaches the document.

### Example

```html
<div id="parent">

    <button id="child">Click Me</button>

</div>

<script>

document.getElementById("parent").addEventListener("click", function() {

    console.log("Parent Clicked");

});

document.getElementById("child").addEventListener("click", function() {

    console.log("Button Clicked");

});

</script>
```

### Output

```text
Button Clicked
Parent Clicked
```

### Explanation

- The button receives the click first.
- The event then bubbles up to the parent `<div>`.
- Finally, it continues toward higher-level elements.

### Key Points

- Default event propagation behavior.
- Travels from child to parent.
- Useful for event delegation.
- Can be stopped using `stopPropagation()`.

### Interview Tip

Remember:

**Event Bubbling = Bottom → Top**

---

# Q84. What is event capturing?

## Answer

**Event capturing** (also called **capturing phase**) is the event propagation mechanism in which an event travels from the outermost parent element down to the target element.

Unlike event bubbling, capturing moves from parent to child.

### Example

```html
<div id="parent">

    <button id="child">Click Me</button>

</div>

<script>

document.getElementById("parent").addEventListener("click", function() {

    console.log("Parent Clicked");

}, true);

document.getElementById("child").addEventListener("click", function() {

    console.log("Button Clicked");

}, true);

</script>
```

### Output

```text
Parent Clicked
Button Clicked
```

### Explanation

- The event starts from the outer parent.
- It travels downward to the target element.
- Capturing occurs only when the third parameter of `addEventListener()` is set to `true`.

### Key Points

- Travels from parent to child.
- Opposite of event bubbling.
- Less commonly used than bubbling.
- Enabled using `addEventListener(..., true)`.

### Interview Tip

Remember:

- **Capturing → Top to Bottom**
- **Bubbling → Bottom to Top**

---

# Q85. What is event delegation?

## Answer

**Event delegation** is a technique in which a single event listener is attached to a parent element instead of attaching separate listeners to multiple child elements.

The parent handles events for its child elements using event bubbling.

### Example

```html
<ul id="menu">

    <li>Home</li>

    <li>About</li>

    <li>Contact</li>

</ul>

<script>

document.getElementById("menu").addEventListener("click", function(event) {

    console.log(event.target.textContent);

});

</script>
```

### Output

```text
Home

or

About

or

Contact
```

### Explanation

- Only one event listener is attached to the `<ul>` element.
- Clicking any `<li>` triggers the parent listener.
- `event.target` identifies the clicked child element.

### Key Points

- Uses event bubbling.
- Improves performance.
- Reduces memory usage.
- Simplifies handling dynamically added elements.

### Interview Tip

Event delegation is commonly used when working with large lists or dynamically created elements because it avoids attaching multiple event listeners.

---

---

# Q86. What is the difference between `preventDefault()` and `stopPropagation()`?

## Answer

Both `preventDefault()` and `stopPropagation()` are methods used while handling events, but they perform different tasks.

- `preventDefault()` prevents the browser's default behavior.
- `stopPropagation()` prevents the event from propagating to parent elements.

### Example Using `preventDefault()`

```html
<a href="https://www.google.com" id="link">Google</a>

<script>

document.getElementById("link").addEventListener("click", function(event) {

    event.preventDefault();

    console.log("Navigation Prevented");

});

</script>
```

### Output

```text
Navigation Prevented
```

### Example Using `stopPropagation()`

```html
<div id="parent">

    <button id="child">Click</button>

</div>

<script>

document.getElementById("parent").addEventListener("click", function() {

    console.log("Parent Clicked");

});

document.getElementById("child").addEventListener("click", function(event) {

    event.stopPropagation();

    console.log("Button Clicked");

});

</script>
```

### Output

```text
Button Clicked
```

### Difference Between `preventDefault()` and `stopPropagation()`

| `preventDefault()` | `stopPropagation()` |
|--------------------|---------------------|
| Stops the browser's default action | Stops event propagation |
| Does not stop bubbling | Stops bubbling or capturing |
| Used for forms and links | Used for nested elements |

### Key Points

- `preventDefault()` prevents the browser's default behavior.
- `stopPropagation()` prevents event propagation.
- Both methods are commonly used in event handling.
- They can also be used together when required.

### Interview Tip

Remember:

- **preventDefault() → Stops Default Browser Action**
- **stopPropagation() → Stops Event Flow**

---

# Q87. What is localStorage?

## Answer

`localStorage` is a browser storage mechanism that allows JavaScript to store data as key-value pairs.

The stored data remains available even after the browser is closed and reopened until it is manually removed.

### Syntax

```javascript
localStorage.setItem(key, value);

localStorage.getItem(key);

localStorage.removeItem(key);

localStorage.clear();
```

### Example

```javascript
localStorage.setItem("name", "Basha");

console.log(localStorage.getItem("name"));
```

### Output

```text
Basha
```

### Explanation

- `setItem()` stores data.
- `getItem()` retrieves stored data.
- Data persists even after closing the browser.

### Key Points

- Stores key-value pairs.
- Data persists until manually removed.
- Available only in the same browser.
- Data is stored as strings.

### Interview Tip

Remember:

**localStorage stores data permanently until it is deleted.**

---

# Q88. What is sessionStorage?

## Answer

`sessionStorage` is a browser storage mechanism used to store data for a single browser session.

The stored data is automatically removed when the browser tab or window is closed.

### Syntax

```javascript
sessionStorage.setItem(key, value);

sessionStorage.getItem(key);

sessionStorage.removeItem(key);

sessionStorage.clear();
```

### Example

```javascript
sessionStorage.setItem("course", "JavaScript");

console.log(sessionStorage.getItem("course"));
```

### Output

```text
JavaScript
```

### Explanation

- Data is available while the browser tab remains open.
- Closing the tab automatically removes the stored data.

### Difference Between localStorage and sessionStorage

| localStorage | sessionStorage |
|--------------|----------------|
| Permanent storage | Temporary storage |
| Survives browser restart | Removed when the tab closes |
| Shared across tabs of the same origin | Limited to the current tab |

### Key Points

- Stores key-value pairs.
- Data exists only during the current session.
- Automatically cleared after closing the tab.
- Data is stored as strings.

### Interview Tip

Remember:

- **localStorage → Permanent**
- **sessionStorage → Temporary**

---

# Q89. What are cookies?

## Answer

Cookies are small pieces of data stored in the browser by websites.

They are commonly used to store user preferences, login information, session IDs, and tracking information.

Unlike localStorage and sessionStorage, cookies are sent to the server with every HTTP request.

### Example

```javascript
document.cookie = "username=Basha";
```

### Reading Cookies

```javascript
console.log(document.cookie);
```

### Output

```text
username=Basha
```

### Key Points

- Stored in the browser.
- Sent to the server with each request.
- Can have an expiration date.
- Commonly used for authentication and session management.

### Difference Between Cookies and localStorage

| Cookies | localStorage |
|----------|--------------|
| Sent to the server | Not sent automatically |
| Small storage size | Larger storage capacity |
| Can expire automatically | Persists until removed |

### Interview Tip

Cookies are mainly used for **authentication and session management**, whereas localStorage is commonly used for storing client-side application data.

---

# Q90. What is debouncing?

## Answer

**Debouncing** is a performance optimization technique that delays the execution of a function until a specified period has passed since the last event occurred.

It prevents a function from being called repeatedly during continuous events such as typing or resizing.

### Example

```javascript
function debounce(callback, delay) {

    let timer;

    return function() {

        clearTimeout(timer);

        timer = setTimeout(callback, delay);

    };

}

const search = debounce(function() {

    console.log("Searching...");

}, 1000);
```

### Explanation

- Every new event resets the timer.
- The callback executes only after the user stops triggering the event.
- This reduces unnecessary function calls.

### Common Use Cases

- Search boxes
- Auto-suggestions
- Window resizing
- Form validation

### Key Points

- Delays function execution.
- Improves application performance.
- Reduces unnecessary API calls.
- Commonly used with input events.

### Interview Tip

Remember:

**Debouncing waits until the user stops performing an action before executing the function.**

---

---

# Q91. What is throttling?

## Answer

**Throttling** is a performance optimization technique that limits how often a function can execute within a specified time interval.

Unlike debouncing, throttling allows the function to execute at regular intervals even if the event continues to occur.

### Example

```javascript
function throttle(callback, delay) {

    let allowExecution = true;

    return function() {

        if (!allowExecution) {

            return;

        }

        callback();

        allowExecution = false;

        setTimeout(function() {

            allowExecution = true;

        }, delay);

    };

}

const logMessage = throttle(function() {

    console.log("Function Executed");

}, 2000);
```

### Explanation

- The function executes immediately.
- Further calls are ignored until the specified delay has passed.
- After the delay, the function can execute again.

### Common Use Cases

- Scrolling events
- Window resizing
- Mouse movement
- Button click protection

### Key Points

- Limits function execution.
- Improves application performance.
- Executes at fixed intervals.
- Prevents excessive function calls.

### Interview Tip

Remember:

- **Debouncing → Executes after the user stops.**
- **Throttling → Executes at regular intervals.**

---

# Q92. What is memoization?

## Answer

**Memoization** is an optimization technique that stores the results of expensive function calls so that future calls with the same input return the stored result instead of recalculating it.

This improves application performance.

### Example

```javascript
function memoizedSquare() {

    const cache = {};

    return function(number) {

        if (cache[number]) {

            return cache[number];

        }

        cache[number] = number * number;

        return cache[number];

    };

}

const square = memoizedSquare();

console.log(square(5));

console.log(square(5));
```

### Output

```text
25
25
```

### Explanation

- The first call calculates the result.
- The result is stored in the cache.
- The second call returns the cached value instead of recalculating it.

### Key Points

- Stores previously computed results.
- Improves performance.
- Avoids repeated calculations.
- Commonly used in recursive algorithms and expensive computations.

### Interview Tip

Memoization is useful when the same function is called multiple times with identical input values.

---

# Q93. What is currying?

## Answer

**Currying** is a technique in JavaScript where a function with multiple parameters is converted into a sequence of functions, each accepting one parameter.

### Example

```javascript
function multiply(a) {

    return function(b) {

        return a * b;

    };

}

const double = multiply(2);

console.log(double(5));
```

### Output

```text
10
```

### Explanation

- The first function receives `2`.
- It returns another function.
- The second function receives `5`.
- The final result is `10`.

### Key Points

- Converts one function into multiple smaller functions.
- Improves code reusability.
- Supports partial function application.
- Frequently used in functional programming.

### Interview Tip

Currying allows you to create specialized functions by fixing one or more arguments in advance.

---

# Q94. What is prototype inheritance?

## Answer

**Prototype inheritance** is the mechanism through which one JavaScript object can inherit properties and methods from another object using its prototype.

Every JavaScript object has an internal link to another object called its prototype.

### Example

```javascript
const person = {

    greet: function() {

        console.log("Hello");

    }

};

const student = Object.create(person);

student.greet();
```

### Output

```text
Hello
```

### Explanation

- `student` is created using `person` as its prototype.
- Since `student` does not have its own `greet()` method, JavaScript searches the prototype.
- The inherited method is executed.

### Key Points

- Objects inherit from other objects.
- Uses the prototype chain.
- Enables code reuse.
- Forms the foundation of inheritance in JavaScript.

### Interview Tip

JavaScript uses **prototype-based inheritance**, not class-based inheritance like Java or C++.

---

# Q95. What is prototypal inheritance?

## Answer

**Prototypal inheritance** is the inheritance model used by JavaScript in which objects inherit properties and methods directly from other objects through the prototype chain.

Prototype inheritance and prototypal inheritance are closely related concepts, but prototypal inheritance refers to the overall inheritance model used by JavaScript.

### Example

```javascript
const animal = {

    sound: "Generic Sound"

};

const dog = Object.create(animal);

dog.name = "Tommy";

console.log(dog.sound);

console.log(dog.name);
```

### Output

```text
Generic Sound
Tommy
```

### Explanation

- `dog` inherits the `sound` property from `animal`.
- The `name` property belongs only to `dog`.
- JavaScript searches the prototype chain when a property is not found on the object itself.

### Key Points

- JavaScript follows prototypal inheritance.
- Objects inherit directly from other objects.
- Uses the prototype chain for property lookup.
- Supports code reuse and flexible object creation.

### Interview Tip

When an object cannot find a property, JavaScript automatically searches its prototype chain until the property is found or the chain ends.

---

---

# Q96. What are classes in JavaScript?

## Answer

Classes are a modern way of creating objects in JavaScript. They provide a cleaner and more readable syntax for working with constructor functions and prototype-based inheritance.

Classes were introduced in **ES6 (ECMAScript 2015)**.

### Syntax

```javascript
class ClassName {

    constructor(parameter) {

        this.parameter = parameter;

    }

    methodName() {

        // Code

    }

}
```

### Example

```javascript
class Student {

    constructor(name) {

        this.name = name;

    }

    display() {

        console.log("Student Name:", this.name);

    }

}

const student1 = new Student("Basha");

student1.display();
```

### Output

```text
Student Name: Basha
```

### Explanation

- The `class` keyword creates a class.
- The `constructor()` initializes object properties.
- `new` creates an object from the class.
- Methods are shared through the prototype.

### Key Points

- Introduced in ES6.
- Provides cleaner syntax.
- Uses prototype-based inheritance internally.
- Supports constructors, methods, inheritance, and static methods.

### Interview Tip

Although JavaScript has classes, they are **syntactic sugar** over the existing prototype-based inheritance system.

---

# Q97. What is garbage collection?

## Answer

Garbage collection is the automatic process of removing objects from memory that are no longer being used by the program.

JavaScript automatically manages memory, so developers do not need to manually free unused memory.

### Example

```javascript
let person = {

    name: "Basha"

};

person = null;
```

### Explanation

- Initially, the object is stored in memory.
- After assigning `null`, there is no reference to the object.
- The JavaScript engine automatically removes the unused object during garbage collection.

### Key Points

- Automatic memory management.
- Removes unused objects.
- Prevents memory leaks.
- Performed by the JavaScript engine.

### Interview Tip

JavaScript uses automatic garbage collection, unlike languages such as C or C++, where memory must be managed manually.

---

# Q98. How does JavaScript manage memory?

## Answer

JavaScript automatically allocates memory when objects are created and automatically releases memory when objects are no longer reachable.

Memory management is handled by the JavaScript engine.

### Example

```javascript
let numbers = [10, 20, 30];

numbers = null;
```

### Explanation

- Memory is allocated when the array is created.
- After assigning `null`, the array becomes unreachable.
- The garbage collector later frees the memory.

### Memory Lifecycle

1. Memory Allocation
2. Memory Usage
3. Memory Release (Garbage Collection)

### Key Points

- Memory allocation is automatic.
- Memory release is automatic.
- Developers should remove unnecessary references.
- Efficient memory usage improves application performance.

### Interview Tip

Memory leaks usually occur when objects are unintentionally kept referenced, preventing the garbage collector from removing them.

---

# Q99. What are CommonJS and ES Modules?

## Answer

Both CommonJS and ES Modules are module systems used to organize JavaScript code into reusable files.

### CommonJS

CommonJS is primarily used in Node.js.

**Example**

```javascript
// math.js

function add(a, b) {

    return a + b;

}

module.exports = add;
```

```javascript
// app.js

const add = require("./math");

console.log(add(10, 20));
```

### ES Modules (ESM)

ES Modules are the standard module system introduced in ES6.

**Example**

```javascript
// math.js

export function add(a, b) {

    return a + b;

}
```

```javascript
// app.js

import { add } from "./math.js";

console.log(add(10, 20));
```

### Output

```text
30
```

### Difference Between CommonJS and ES Modules

| CommonJS | ES Modules |
|-----------|------------|
| Uses `require()` | Uses `import` |
| Uses `module.exports` | Uses `export` |
| Mainly used in Node.js | Standard JavaScript module system |
| Loaded synchronously | Supports static analysis and modern tooling |

### Key Points

- Both organize reusable code.
- CommonJS is common in older Node.js projects.
- ES Modules are the modern JavaScript standard.
- Most modern applications prefer ES Modules.

### Interview Tip

For modern JavaScript development, **ES Modules (`import` and `export`) are the recommended approach.**

---

# Q100. What are the latest JavaScript features introduced in ES2025 and beyond?

## Answer

JavaScript continues to evolve through yearly ECMAScript (ES) releases.

Recent and upcoming versions introduce new language features that improve readability, developer productivity, and application performance.

Some notable modern JavaScript features include:

- Improved `Set` methods
- Better iterator helper methods
- Enhanced regular expressions
- Improved error handling
- Performance improvements
- Better module support
- Ongoing enhancements to arrays, promises, and asynchronous programming

### Example

```javascript
const numbers = [1, 2, 3, 4, 5];

const evenNumbers = numbers.filter(function(number) {

    return number % 2 === 0;

});

console.log(evenNumbers);
```

### Output

```text
[2, 4]
```

### Explanation

Modern ECMAScript versions continue to improve existing language features while maintaining backward compatibility.

Developers should regularly update their knowledge to take advantage of new capabilities.

### Key Points

- ECMAScript is updated every year.
- New features improve performance and developer experience.
- Modern browsers regularly adopt new JavaScript features.
- Keeping up with ECMAScript releases is important for JavaScript developers.

### Interview Tip

For freshers, focus first on **ES6 through the latest stable ECMAScript features** such as `let`, `const`, arrow functions, classes, promises, modules, async/await, optional chaining, nullish coalescing, and then gradually learn newer additions introduced in recent ECMAScript versions.

---
