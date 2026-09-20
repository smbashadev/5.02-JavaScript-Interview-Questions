# Functions & Objects Interview Questions (21–40)

This document contains the most frequently asked **JavaScript Functions & Objects Interview Questions**. The answers are written in simple, beginner-friendly language to help students, freshers, and developers prepare confidently for technical interviews.

---

# Q21. What is a function?

## Answer

A **function** is a reusable block of code that performs a specific task.

Instead of writing the same code multiple times, you can write it once inside a function and call it whenever needed.

Functions improve code reusability, readability, and maintainability.

### Syntax

```javascript
function functionName() {

    // Code

}
```

### Example

```javascript
function greet() {

    console.log("Welcome to JavaScript");

}

greet();
```

### Output

```text
Welcome to JavaScript
```

### Key Points

- A function is a reusable block of code.
- Functions execute only when they are called.
- A function can accept parameters and return values.
- Functions reduce code duplication.

### Interview Tip

A function is one of the most fundamental concepts in JavaScript. Always mention that it is a reusable block of code that performs a specific task.

---

# Q22. What is a function expression?

## Answer

A **function expression** is a function that is assigned to a variable.

Unlike a function declaration, a function expression is stored inside a variable and can be used whenever required.

### Syntax

```javascript
const variableName = function() {

    // Code

};
```

### Example

```javascript
const greet = function() {

    console.log("Hello, JavaScript!");

};

greet();
```

### Output

```text
Hello, JavaScript!
```

### Difference Between Function Declaration and Function Expression

| Function Declaration | Function Expression |
|----------------------|---------------------|
| Declared using the `function` keyword | Assigned to a variable |
| Can be called before declaration due to hoisting | Cannot be called before declaration |
| Has a function name | May be anonymous or named |

### Key Points

- Stored inside a variable.
- Can be anonymous.
- Not fully hoisted like function declarations.
- Frequently used in modern JavaScript.

### Interview Tip

Interviewers often ask the difference between a function declaration and a function expression. Explain both with a simple example.

---

# Q23. What are arrow functions?

## Answer

Arrow functions are a shorter and cleaner way to write functions in JavaScript.

They were introduced in **ES6 (ECMAScript 2015)**.

Arrow functions automatically inherit the `this` value from their surrounding scope, making them useful in many situations.

### Syntax

```javascript
const functionName = () => {

    // Code

};
```

### Example

```javascript
const greet = () => {

    console.log("Welcome");

};

greet();
```

### Output

```text
Welcome
```

### Example with Parameters

```javascript
const add = (a, b) => a + b;

console.log(add(10, 20));
```

### Output

```text
30
```

### Key Points

- Introduced in ES6.
- Shorter syntax than regular functions.
- Uses the `=>` operator.
- Does not have its own `this`.
- Commonly used in callbacks and array methods.

### Interview Tip

Arrow functions are ideal for short functions and callbacks, but avoid using them as object methods when you need the object's own `this` value.

---

# Q24. What is an IIFE (Immediately Invoked Function Expression)?

## Answer

An **Immediately Invoked Function Expression (IIFE)** is a function that executes immediately after it is created.

It is mainly used to avoid polluting the global scope by creating a private scope.

### Syntax

```javascript
(function() {

    // Code

})();
```

### Example

```javascript
(function() {

    console.log("IIFE Executed");

})();
```

### Output

```text
IIFE Executed
```

### Example with Parameters

```javascript
(function(name) {

    console.log("Welcome " + name);

})("Basha");
```

### Output

```text
Welcome Basha
```

### Key Points

- Executes immediately.
- Creates a private scope.
- Helps avoid global variable conflicts.
- Widely used before ES6 modules became available.

### Interview Tip

Remember that an IIFE is executed immediately after it is defined and is enclosed within parentheses.

---

# Q25. What are callback functions?

## Answer

A **callback function** is a function that is passed as an argument to another function and is executed later.

Callbacks are widely used for asynchronous operations, event handling, and array methods.

### Example

```javascript
function greet(name) {

    console.log("Hello " + name);

}

function processUser(callback) {

    callback("Basha");

}

processUser(greet);
```

### Output

```text
Hello Basha
```

### Explanation

- `greet()` is passed as an argument.
- `processUser()` calls the callback function.
- The callback executes only when invoked.

### Key Points

- Passed as an argument to another function.
- Executed after a specific task is completed.
- Commonly used in asynchronous programming.
- Frequently used with `setTimeout()`, events, promises, and array methods.

### Interview Tip

A callback is **not executed immediately**. It is passed to another function and executed when required.

---

---

# Q26. What are higher-order functions?

## Answer

A **higher-order function** is a function that either:

- Accepts one or more functions as arguments, or
- Returns another function as its result.

Higher-order functions make JavaScript more flexible and reusable.

### Example

```javascript
function greet(name) {

    return "Hello " + name;

}

function processUser(callback) {

    console.log(callback("Basha"));

}

processUser(greet);
```

### Output

```text
Hello Basha
```

### Example Using Array Method

```javascript
let numbers = [1, 2, 3, 4, 5];

let squares = numbers.map(function(number) {

    return number * number;

});

console.log(squares);
```

### Output

```text
[1, 4, 9, 16, 25]
```

### Key Points

- Accepts functions as arguments.
- Can return another function.
- Promotes reusable code.
- Commonly used with `map()`, `filter()`, and `reduce()`.

### Interview Tip

Remember:

**Every callback function is used with a higher-order function, but a higher-order function is the function that accepts or returns another function.**

---

# Q27. What are closures?

## Answer

A **closure** is a function that remembers and can access variables from its outer (enclosing) function even after the outer function has finished executing.

Closures help preserve data and create private variables.

### Example

```javascript
function outer() {

    let message = "Hello";

    function inner() {

        console.log(message);

    }

    return inner;

}

const display = outer();

display();
```

### Output

```text
Hello
```

### Explanation

- `inner()` is returned from `outer()`.
- Even after `outer()` finishes execution, `inner()` can still access the `message` variable.
- This behavior is called a closure.

### Key Points

- Remembers variables from the outer function.
- Creates private variables.
- Preserves function state.
- Widely used in JavaScript frameworks and libraries.

### Interview Tip

One of the most common JavaScript interview questions is **"What is a closure?"**

A simple answer is:

> A closure is a function that remembers variables from its outer scope even after the outer function has finished executing.

---

# Q28. What is lexical scope?

## Answer

Lexical scope means that a function can access variables from the scope in which it was defined.

The scope is determined by the position of the function in the source code, not by where it is called.

### Example

```javascript
let language = "JavaScript";

function outer() {

    function inner() {

        console.log(language);

    }

    inner();

}

outer();
```

### Output

```text
JavaScript
```

### Explanation

The `inner()` function can access the variable `language` because it is defined within the scope where `language` is available.

### Key Points

- Scope is determined during code writing.
- Inner functions can access outer variables.
- Forms the foundation of closures.

### Interview Tip

Closures work because of lexical scope. Learn both concepts together because interviewers often ask them in the same discussion.

---

# Q29. What is the `this` keyword?

## Answer

The `this` keyword refers to the object that is currently executing the function.

The value of `this` depends on how the function is called.

### Example

```javascript
const student = {

    name: "Basha",

    greet() {

        console.log(this.name);

    }

};

student.greet();
```

### Output

```text
Basha
```

### Example in a Regular Function

```javascript
function show() {

    console.log(this);

}

show();
```

### Output

```text
Window object (Browser)

or

Global object (Node.js)
```

### Key Points

- Refers to the current object.
- Value depends on how the function is invoked.
- Inside object methods, `this` refers to that object.
- Arrow functions do not have their own `this`.

### Interview Tip

A favorite interview question is:

**Why doesn't an arrow function have its own `this`?**

Answer:

Because it inherits `this` from its surrounding lexical scope.

---

# Q30. What are object literals?

## Answer

An **object literal** is the simplest way to create an object in JavaScript using curly braces `{}`.

Objects store data as **key-value pairs**.

### Syntax

```javascript
const objectName = {

    key: value

};
```

### Example

```javascript
const student = {

    id: 101,

    name: "Basha",

    course: "Java Full Stack"

};

console.log(student);
```

### Output

```text
{
  id: 101,
  name: "Basha",
  course: "Java Full Stack"
}
```

### Accessing Object Properties

```javascript
console.log(student.name);

console.log(student.course);
```

### Output

```text
Basha
Java Full Stack
```

### Key Points

- Created using `{}`.
- Stores data as key-value pairs.
- Properties can be accessed using dot notation or bracket notation.
- Most commonly used way to create objects in JavaScript.

### Interview Tip

Object literals are the easiest and most frequently used way to create objects in JavaScript. Most interview coding examples use object literals.

---

---

# Q31. How do you create objects in JavaScript?

## Answer

JavaScript provides multiple ways to create objects.

The most common methods are:

1. Object Literal
2. Object Constructor
3. Constructor Function
4. ES6 Class
5. Object.create()

### 1. Using Object Literal

```javascript
const student = {

    id: 101,

    name: "Basha"

};

console.log(student);
```

### Output

```text
{ id: 101, name: 'Basha' }
```

### 2. Using the Object Constructor

```javascript
const student = new Object();

student.id = 101;
student.name = "Basha";

console.log(student);
```

### Output

```text
{ id: 101, name: 'Basha' }
```

### 3. Using a Constructor Function

```javascript
function Student(id, name) {

    this.id = id;
    this.name = name;

}

const student = new Student(101, "Basha");

console.log(student);
```

### Output

```text
Student { id: 101, name: 'Basha' }
```

### Key Points

- Object literals are the simplest method.
- Constructor functions create multiple objects.
- ES6 classes are used in modern JavaScript.
- `Object.create()` creates an object using another object as its prototype.

### Interview Tip

Object literals are the most commonly used approach in interviews and real-world applications.

---

# Q32. What is object destructuring?

## Answer

Object destructuring is an ES6 feature that allows you to extract object properties into separate variables.

It makes the code cleaner, shorter, and easier to read.

### Example

```javascript
const student = {

    id: 101,

    name: "Basha",

    course: "Java"

};

const { id, name, course } = student;

console.log(id);
console.log(name);
console.log(course);
```

### Output

```text
101
Basha
Java
```

### Renaming Variables

```javascript
const student = {

    name: "Basha"

};

const { name: studentName } = student;

console.log(studentName);
```

### Output

```text
Basha
```

### Key Points

- Introduced in ES6.
- Extracts object properties into variables.
- Makes code shorter and cleaner.
- Supports variable renaming.

### Interview Tip

Object destructuring is frequently used in React.js and modern JavaScript projects.

---

# Q33. What is the spread operator (`...`)?

## Answer

The spread operator (`...`) is an ES6 feature used to expand the elements of an array or the properties of an object.

It is commonly used for copying, merging, and passing values.

### Example with Arrays

```javascript
const numbers1 = [10, 20, 30];

const numbers2 = [...numbers1, 40, 50];

console.log(numbers2);
```

### Output

```text
[10, 20, 30, 40, 50]
```

### Example with Objects

```javascript
const student = {

    id: 101,

    name: "Basha"

};

const details = {

    ...student,

    city: "Hyderabad"

};

console.log(details);
```

### Output

```text
{
  id: 101,
  name: "Basha",
  city: "Hyderabad"
}
```

### Key Points

- Introduced in ES6.
- Expands arrays and objects.
- Used for copying arrays and objects.
- Used for merging arrays and objects.

### Interview Tip

Remember:

**Spread Operator → Expands values**

---

# Q34. What is the rest operator?

## Answer

The rest operator (`...`) collects multiple values into a single array.

It is commonly used in function parameters and object destructuring.

Although it uses the same syntax as the spread operator, its purpose is different.

### Example

```javascript
function sum(...numbers) {

    console.log(numbers);

}

sum(10, 20, 30, 40);
```

### Output

```text
[10, 20, 30, 40]
```

### Example

```javascript
const [first, ...remaining] = [10, 20, 30, 40];

console.log(first);

console.log(remaining);
```

### Output

```text
10
[20, 30, 40]
```

### Key Points

- Collects multiple values.
- Used in function parameters.
- Returns an array.
- Introduced in ES6.

### Interview Tip

Remember the difference:

- **Spread Operator → Expands values**
- **Rest Operator → Collects values**

---

# Q35. What are default parameters?

## Answer

Default parameters allow you to assign default values to function parameters.

If no argument is passed, the default value is used automatically.

### Syntax

```javascript
function functionName(parameter = defaultValue) {

}
```

### Example

```javascript
function greet(name = "Guest") {

    console.log("Welcome " + name);

}

greet();

greet("Basha");
```

### Output

```text
Welcome Guest
Welcome Basha
```

### Explanation

- When no argument is passed, `"Guest"` is used.
- When an argument is provided, it replaces the default value.

### Key Points

- Introduced in ES6.
- Makes functions more flexible.
- Reduces the need for conditional checks.
- Improves code readability.

### Interview Tip

Default parameters make your functions safer by preventing `undefined` values when arguments are missing.

---

---

# Q36. What is optional chaining (`?.`)?

## Answer

Optional chaining (`?.`) is an ES2020 feature that allows you to safely access nested object properties without causing an error if a property does not exist.

Instead of throwing an error, it returns `undefined`.

### Example

```javascript
const student = {

    name: "Basha",

    address: {

        city: "Hyderabad"

    }

};

console.log(student.address?.city);

console.log(student.contact?.phone);
```

### Output

```text
Hyderabad
undefined
```

### Explanation

- `student.address?.city` exists, so it returns `"Hyderabad"`.
- `student.contact` does not exist, so `undefined` is returned instead of an error.

### Key Points

- Introduced in ES2020.
- Prevents runtime errors.
- Returns `undefined` if the property does not exist.
- Useful for accessing deeply nested objects.

### Interview Tip

Optional chaining helps write safer code by avoiding errors when accessing properties that may not exist.

---

# Q37. What is nullish coalescing (`??`)?

## Answer

The nullish coalescing operator (`??`) returns the right-hand value only when the left-hand value is `null` or `undefined`.

It is commonly used to provide default values.

### Syntax

```javascript
value ?? defaultValue
```

### Example

```javascript
let name = null;

console.log(name ?? "Guest");
```

### Output

```text
Guest
```

### Example

```javascript
let age = 25;

console.log(age ?? 18);
```

### Output

```text
25
```

### Explanation

- If the left value is `null` or `undefined`, the default value is returned.
- Otherwise, the original value is returned.

### Key Points

- Introduced in ES2020.
- Works only with `null` and `undefined`.
- Useful for assigning default values.
- Different from the logical OR (`||`) operator.

### Interview Tip

Remember the difference:

- `||` checks for all falsy values (`0`, `false`, `""`, `null`, `undefined`, `NaN`).
- `??` checks only for `null` and `undefined`.

---

# Q38. What are object methods?

## Answer

An object method is a function stored as a property of an object.

Methods allow objects to perform actions.

### Example

```javascript
const student = {

    name: "Basha",

    greet: function() {

        console.log("Welcome " + this.name);

    }

};

student.greet();
```

### Output

```text
Welcome Basha
```

### Example Using Method Shorthand

```javascript
const calculator = {

    add(a, b) {

        return a + b;

    }

};

console.log(calculator.add(10, 20));
```

### Output

```text
30
```

### Key Points

- Methods are functions inside objects.
- Methods define object behavior.
- `this` usually refers to the current object.
- Method shorthand was introduced in ES6.

### Interview Tip

An object property stores data, whereas an object method performs an action.

---

# Q39. What is method chaining?

## Answer

Method chaining is a programming technique where multiple methods are called one after another on the same object.

Each method returns the object itself (`this`), allowing the next method to be called immediately.

### Example

```javascript
const calculator = {

    value: 0,

    add(num) {

        this.value += num;
        return this;

    },

    subtract(num) {

        this.value -= num;
        return this;

    },

    display() {

        console.log(this.value);
        return this;

    }

};

calculator.add(10).subtract(3).display();
```

### Output

```text
7
```

### Explanation

- `add()` returns the object.
- `subtract()` is called on the returned object.
- `display()` is then called on the same object.

### Key Points

- Improves code readability.
- Reduces repetitive object references.
- Requires methods to return `this`.
- Commonly used in libraries like jQuery.

### Interview Tip

Method chaining works because each method returns the current object (`this`).

---

# Q40. What is object freezing and sealing?

## Answer

JavaScript provides two methods to control object modification:

- `Object.freeze()`
- `Object.seal()`

### Object.freeze()

`Object.freeze()` prevents:

- Adding new properties
- Updating existing properties
- Deleting properties

### Example

```javascript
const student = {

    name: "Basha"

};

Object.freeze(student);

student.name = "Rahul";

console.log(student.name);
```

### Output

```text
Basha
```

### Object.seal()

`Object.seal()` allows updating existing properties but does not allow adding or deleting properties.

### Example

```javascript
const student = {

    name: "Basha"

};

Object.seal(student);

student.name = "Rahul";

console.log(student.name);
```

### Output

```text
Rahul
```

### Difference Between Freeze and Seal

| Object.freeze() | Object.seal() |
|-----------------|---------------|
| Cannot add properties | Cannot add properties |
| Cannot update properties | Can update existing properties |
| Cannot delete properties | Cannot delete properties |
| Completely immutable | Partially mutable |

### Key Points

- `Object.freeze()` makes an object completely immutable.
- `Object.seal()` allows updating existing properties.
- Both prevent adding and deleting properties.
- Useful for protecting object data.

### Interview Tip

A common interview question is:

**Which is more restrictive: `Object.freeze()` or `Object.seal()`?**

Answer:

`Object.freeze()` is more restrictive because it prevents adding, updating, and deleting properties, whereas `Object.seal()` still allows updating existing properties.

---
