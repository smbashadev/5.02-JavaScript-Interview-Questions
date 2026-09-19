# JavaScript Fundamentals Interview Questions (1–20)

This document contains the most frequently asked **JavaScript Fundamentals Interview Questions**. The answers are written in simple, beginner-friendly language to help students, freshers, and developers prepare confidently for technical interviews.

---

# Q1. What is JavaScript?

## Answer

JavaScript is a **high-level, lightweight, interpreted, and dynamically typed programming language** used to create interactive and dynamic web pages.

It is one of the three core technologies of web development:

- **HTML** – Creates the structure of a web page.
- **CSS** – Styles the web page.
- **JavaScript** – Adds interactivity and functionality.

JavaScript is widely used for:

- Frontend Development
- Backend Development (Node.js)
- Mobile Application Development
- Desktop Application Development
- Game Development

### Example

```javascript
console.log("Hello, JavaScript!");
```

### Output

```text
Hello, JavaScript!
```

### Key Points

- High-level programming language.
- Lightweight and easy to learn.
- Dynamically typed language.
- Runs in browsers and servers.
- Makes web pages interactive.

### Interview Tip

When answering this question, explain:
- What JavaScript is.
- Where it is used.
- Why it is important.

---

# Q2. What are the different data types in JavaScript?

## Answer

A **data type** defines the type of value that a variable can store.

JavaScript has **two categories of data types**.

### Primitive Data Types

- String
- Number
- BigInt
- Boolean
- Undefined
- Null
- Symbol

### Non-Primitive (Reference) Data Types

- Object
- Array
- Function
- Date
- Map
- Set

### Example

```javascript
let name = "Basha";
let age = 24;
let isPlaced = true;
let student = {
    id: 101,
    city: "Bangalore"
};

console.log(typeof name);
console.log(typeof age);
console.log(typeof isPlaced);
console.log(typeof student);
```

### Output

```text
string
number
boolean
object
```

### Key Points

- JavaScript has **7 primitive data types**.
- Objects, arrays, and functions are non-primitive data types.
- The `typeof` operator is used to check the data type of a value.

### Interview Tip

Interviewers often ask you to classify data types into **primitive** and **non-primitive** categories. Be prepared to explain the difference with examples.

---

# Q3. What is the difference between `var`, `let`, and `const`?

## Answer

`var`, `let`, and `const` are keywords used to declare variables in JavaScript. They differ in terms of scope, redeclaration, reassignment, and hoisting.

| Feature | var | let | const |
|---------|-----|-----|-------|
| Scope | Function Scope | Block Scope | Block Scope |
| Redeclaration | Yes | No | No |
| Reassignment | Yes | Yes | No |
| Hoisting | Yes | Yes (Temporal Dead Zone) | Yes (Temporal Dead Zone) |

### Example

```javascript
var a = 10;
var a = 20;

let b = 30;

const c = 40;

console.log(a);
console.log(b);
console.log(c);
```

### Output

```text
20
30
40
```

### Key Points

- Use **const** when the value should not change.
- Use **let** when the value may change.
- Avoid using **var** in modern JavaScript.

### Interview Tip

A common interview answer is:

> **Use `const` by default, `let` when reassignment is needed, and avoid `var` unless maintaining legacy code.**

---

# Q4. What are primitive and non-primitive data types?

## Answer

JavaScript data types are divided into **primitive** and **non-primitive (reference)** data types.

### Primitive Data Types

Primitive data types store the **actual value** directly in memory.

They include:

- String
- Number
- BigInt
- Boolean
- Undefined
- Null
- Symbol

### Non-Primitive Data Types

Non-primitive data types store the **reference (memory address)** of the value.

Examples include:

- Object
- Array
- Function
- Map
- Set
- Date

### Example

```javascript
let age = 24;

let student = {
    name: "Basha"
};

console.log(typeof age);
console.log(typeof student);
```

### Output

```text
number
object
```

### Key Points

- Primitive values are immutable.
- Non-primitive values are mutable.
- Objects and arrays are reference types.

### Interview Tip

Remember:

- **Primitive → Stores the actual value**
- **Non-Primitive → Stores the reference (memory address)**

---

# Q5. What is type coercion?

## Answer

Type coercion is the **automatic or explicit conversion of one data type into another**.

JavaScript performs type coercion when different data types are used together in an expression.

There are two types of type coercion:

### 1. Implicit Type Coercion

JavaScript automatically converts one data type into another.

```javascript
console.log("10" + 5);
```

**Output**

```text
105
```

### 2. Explicit Type Conversion

The programmer manually converts the data type using functions like `Number()`, `String()`, or `Boolean()`.

```javascript
let value = "10";

console.log(Number(value));
```

**Output**

```text
10
```

### Example

```javascript
console.log("5" + 2);
console.log("5" - 2);
console.log(true + 1);
```

### Output

```text
52
3
2
```

### Explanation

- `"5" + 2` performs string concatenation.
- `"5" - 2` converts the string into a number before subtraction.
- `true` is automatically converted to `1`.

### Key Points

- JavaScript automatically converts data types when needed.
- The `+` operator performs both addition and string concatenation.
- Explicit conversion produces more predictable results.

### Interview Tip

Type coercion is one of the most frequently tested JavaScript concepts. Practice output-based questions involving strings, numbers, booleans, `null`, and `undefined`.

---

---

# Q6. What is the difference between `==` and `===` in JavaScript?

## Answer

Both `==` and `===` are comparison operators used to compare two values.

- `==` is called the **Loose Equality Operator**. It compares only the values after performing type conversion if required.
- `===` is called the **Strict Equality Operator**. It compares both the value and the data type without performing type conversion.

### Example

```javascript
console.log(10 == "10");
console.log(10 === "10");

console.log(20 == 20);
console.log(20 === 20);
```

### Output

```text
true
false
true
true
```

### Explanation

- `10 == "10"` returns `true` because JavaScript converts the string `"10"` into the number `10`.
- `10 === "10"` returns `false` because one value is a number and the other is a string.
- `20 === 20` returns `true` because both the value and the data type are the same.

### Key Points

- `==` compares only the values.
- `===` compares both the value and the data type.
- `===` is recommended because it prevents unexpected results caused by automatic type conversion.

### Interview Tip

Always use **`===`** in real-world applications unless you specifically need type conversion.

---

# Q7. What is Hoisting in JavaScript?

## Answer

Hoisting is JavaScript's default behavior of moving **variable and function declarations** to the top of their scope before executing the code.

Only declarations are hoisted, not initializations.

### Example

```javascript
console.log(message);

var message = "Hello";
```

### Output

```text
undefined
```

### Explanation

JavaScript internally treats the above code like this:

```javascript
var message;

console.log(message);

message = "Hello";
```

Since the variable exists but has not been assigned a value, the output is `undefined`.

### Example using `let`

```javascript
console.log(age);

let age = 24;
```

### Output

```text
ReferenceError: Cannot access 'age' before initialization
```

### Key Points

- `var` variables are hoisted and initialized with `undefined`.
- `let` and `const` are hoisted but remain in the **Temporal Dead Zone (TDZ)** until they are initialized.
- Function declarations are completely hoisted.

### Interview Tip

Remember:

- **var → Hoisted + initialized with `undefined`**
- **let & const → Hoisted but inaccessible before declaration**

---

# Q8. What is the scope of a variable in JavaScript?

## Answer

Scope determines where a variable can be accessed within a program.

JavaScript has three types of scope.

### 1. Global Scope

A variable declared outside all functions and blocks can be accessed anywhere in the program.

### Example

```javascript
let company = "OpenAI";

function showCompany() {
    console.log(company);
}

showCompany();
```

### Output

```text
OpenAI
```

---

### 2. Function Scope

Variables declared using `var` inside a function can be accessed only within that function.

### Example

```javascript
function demo() {
    var number = 100;
    console.log(number);
}

demo();
```

### Output

```text
100
```

---

### 3. Block Scope

Variables declared using `let` and `const` inside a block can be accessed only within that block.

### Example

```javascript
{
    let city = "Bangalore";
    console.log(city);
}
```

### Output

```text
Bangalore
```

### Key Points

- Global variables are accessible throughout the program.
- Function-scoped variables exist only inside functions.
- Block-scoped variables exist only inside blocks.

### Interview Tip

Prefer `let` and `const` because they support block scope and help avoid accidental bugs.

---

# Q9. What is the difference between `null` and `undefined`?

## Answer

Both `null` and `undefined` represent the absence of a value, but they have different meanings.

| null | undefined |
|------|-----------|
| Assigned intentionally | Assigned automatically |
| Represents an empty value | Represents a variable without a value |
| `typeof null` returns `object` | `typeof undefined` returns `undefined` |

### Example

```javascript
let name = null;
let age;

console.log(name);
console.log(age);
```

### Output

```text
null
undefined
```

### Example

```javascript
console.log(typeof null);
console.log(typeof undefined);
```

### Output

```text
object
undefined
```

### Key Points

- `null` is assigned intentionally.
- `undefined` is assigned automatically.
- Both represent missing values but are used in different situations.

### Interview Tip

If asked why `typeof null` returns `object`, explain that it is a historical bug in JavaScript that has been preserved for backward compatibility.

---

# Q10. What are JavaScript operators?

## Answer

Operators are special symbols used to perform operations on variables and values.

JavaScript provides different types of operators.

### Arithmetic Operators

```javascript
+
-
*
/
%
**
```

### Assignment Operators

```javascript
=
+=
-=
*=
/=
%=
```

### Comparison Operators

```javascript
==
===
!=
!==
>
<
>=
<=
```

### Logical Operators

```javascript
&&
||
!
```

### Example

```javascript
let a = 20;
let b = 10;

console.log(a + b);
console.log(a > b);
console.log(a == b);
console.log(a != b);
```

### Output

```text
30
true
false
true
```

### Key Points

- Arithmetic operators perform mathematical calculations.
- Assignment operators assign values.
- Comparison operators compare values.
- Logical operators evaluate multiple conditions.

### Interview Tip

Practice output-based questions that combine arithmetic, comparison, and logical operators, as they are frequently asked in JavaScript interviews.

---

---

# Q11. What is the difference between `let`, `const`, and `var` scope?

## Answer

The scope of a variable determines where it can be accessed in a program.

- `var` has **function scope**.
- `let` has **block scope**.
- `const` also has **block scope**.

### Example

```javascript
function demo() {

    if (true) {

        var a = 10;
        let b = 20;
        const c = 30;
    }

    console.log(a);

    // console.log(b);

    // console.log(c);
}

demo();
```

### Output

```text
10
ReferenceError
ReferenceError
```

### Explanation

- `a` is accessible because `var` has function scope.
- `b` and `c` are not accessible outside the block because they have block scope.

### Key Points

- `var` → Function Scope
- `let` → Block Scope
- `const` → Block Scope
- Prefer `let` and `const` in modern JavaScript.

### Interview Tip

Interviewers frequently ask the difference between function scope and block scope. Always explain with an example.

---

# Q12. What is the `typeof` operator?

## Answer

The `typeof` operator is used to determine the data type of a variable or value.

### Example

```javascript
let name = "Basha";
let age = 24;
let isPlaced = true;
let student = {};

console.log(typeof name);
console.log(typeof age);
console.log(typeof isPlaced);
console.log(typeof student);
```

### Output

```text
string
number
boolean
object
```

### More Examples

```javascript
console.log(typeof undefined);

console.log(typeof null);

console.log(typeof []);

console.log(typeof function(){});
```

### Output

```text
undefined
object
object
function
```

### Key Points

- Returns the data type of a value.
- Arrays return `object`.
- `null` returns `object` (historical JavaScript behavior).
- Functions return `function`.

### Interview Tip

Remember these special cases:

- `typeof null` → object
- `typeof []` → object
- `typeof function(){}` → function

---

# Q13. What is a JavaScript identifier?

## Answer

An identifier is the name given to variables, functions, classes, objects, or other user-defined elements in JavaScript.

### Valid Identifiers

```javascript
let studentName;

let age;

let totalMarks;

function calculateSum() {

}
```

### Invalid Identifiers

```javascript
let 123name;

let first-name;

let class;
```

### Identifier Rules

- Must begin with a letter, underscore (`_`), or dollar sign (`$`).
- Cannot start with a number.
- Cannot contain spaces.
- Cannot use JavaScript reserved keywords.
- JavaScript identifiers are case-sensitive.

### Example

```javascript
let studentName = "Basha";

console.log(studentName);
```

### Output

```text
Basha
```

### Key Points

- Identifiers are user-defined names.
- Follow JavaScript naming conventions.
- Use meaningful names.

### Interview Tip

Use **camelCase** naming for variables and functions.

Example:

```javascript
let firstName;

let totalSalary;

function calculateTotal() {

}
```

---

# Q14. What are JavaScript keywords?

## Answer

Keywords are reserved words that have predefined meanings in JavaScript.

They cannot be used as variable names, function names, or identifiers.

### Common JavaScript Keywords

```text
let
const
var
if
else
switch
case
default
for
while
do
break
continue
return
function
class
extends
new
this
super
try
catch
finally
throw
import
export
```

### Example

```javascript
let age = 24;

if(age >= 18){

    console.log("Eligible");

}
```

### Output

```text
Eligible
```

### Key Points

- Keywords are reserved by JavaScript.
- Their meaning cannot be changed.
- They cannot be used as identifiers.

### Interview Tip

Interviewers may ask you to differentiate between **keywords** and **identifiers**.

---

# Q15. What are JavaScript comments?

## Answer

Comments are used to explain code or temporarily disable code during development.

JavaScript supports two types of comments.

### Single-Line Comment

```javascript
// This is a single-line comment

let age = 24;
```

### Multi-Line Comment

```javascript
/*
This is a
multi-line comment.
*/

let name = "Basha";
```

### Example

```javascript
// Display a welcome message

console.log("Welcome to JavaScript");
```

### Output

```text
Welcome to JavaScript
```

### Advantages

- Improves code readability.
- Helps explain complex logic.
- Makes code easier to maintain.
- Useful for debugging.

### Key Points

- `//` is used for single-line comments.
- `/* */` is used for multi-line comments.
- Comments are ignored by the JavaScript engine.

### Interview Tip

Write meaningful comments only when necessary. Good code should be self-explanatory, and comments should clarify complex logic rather than describe obvious statements.

---

---

# Q16. What is a JavaScript statement?

## Answer

A **statement** is a single instruction that tells the JavaScript engine to perform a specific task.

A JavaScript program is made up of one or more statements.

### Example

```javascript
let name = "Basha";

console.log(name);

let age = 24;

console.log(age);
```

### Output

```text
Basha
24
```

### Explanation

Each line of code above is a separate JavaScript statement.

### Key Points

- A statement performs an action.
- A JavaScript program contains multiple statements.
- Statements are usually terminated with a semicolon (`;`), although JavaScript inserts semicolons automatically in many cases.

### Interview Tip

A statement performs an action, whereas an expression produces a value.

---

# Q17. What is an expression in JavaScript?

## Answer

An **expression** is a combination of values, variables, operators, and function calls that produces a single value.

Expressions can be assigned to variables, passed as function arguments, or used in conditions.

### Example

```javascript
let result = 10 + 20;

console.log(result);
```

### Output

```text
30
```

### More Examples

```javascript
5 * 10

age >= 18

a + b

true && false
```

Each of the above is a valid JavaScript expression because it produces a value.

### Key Points

- Expressions always return a value.
- They can contain variables, literals, operators, and function calls.
- Expressions are commonly used in assignments and conditions.

### Interview Tip

Remember the difference:

- **Statement → Performs an action**
- **Expression → Produces a value**

---

# Q18. What are literals in JavaScript?

## Answer

A **literal** is a fixed value that is written directly in the source code.

JavaScript supports different types of literals.

### Numeric Literal

```javascript
100
25.5
```

### String Literal

```javascript
"Hello"

'JavaScript'
```

### Boolean Literal

```javascript
true

false
```

### Object Literal

```javascript
{
    name: "Basha",
    age: 24
}
```

### Array Literal

```javascript
[10, 20, 30]
```

### Example

```javascript
let city = "Hyderabad";

let age = 24;

let isPlaced = true;

console.log(city);
console.log(age);
console.log(isPlaced);
```

### Output

```text
Hyderabad
24
true
```

### Key Points

- Literals are fixed values.
- They are written directly in the code.
- JavaScript supports numeric, string, boolean, object, array, and other literals.

### Interview Tip

Whenever you directly write a value in code, such as `100`, `"Hello"`, or `true`, it is called a literal.

---

# Q19. What are reserved words in JavaScript?

## Answer

Reserved words are predefined words that have special meanings in JavaScript.

They cannot be used as variable names, function names, or identifiers.

### Examples

```text
let

const

var

if

else

for

while

switch

case

return

class

new

this

try

catch

finally

import

export
```

### Invalid Example

```javascript
let class = "Java";
```

### Output

```text
SyntaxError
```

### Valid Example

```javascript
let course = "Java";

console.log(course);
```

### Output

```text
Java
```

### Key Points

- Reserved words have predefined meanings.
- They cannot be used as identifiers.
- Using reserved words as variable names results in a syntax error.

### Interview Tip

Keywords and reserved words are often considered the same in interviews. Learn the most commonly used reserved words.

---

# Q20. Why is JavaScript called a dynamically typed language?

## Answer

JavaScript is called a **dynamically typed language** because the data type of a variable is determined at runtime.

A variable can store different types of values during program execution without explicitly declaring its data type.

### Example

```javascript
let value = 100;

console.log(value);

value = "JavaScript";

console.log(value);

value = true;

console.log(value);
```

### Output

```text
100
JavaScript
true
```

### Explanation

The variable `value` first stores a number, then a string, and finally a boolean value.

JavaScript automatically changes the variable's data type at runtime.

### Key Points

- No need to declare the data type explicitly.
- Variables can store different types of values.
- Data types are checked during execution.
- Makes JavaScript flexible and easy to write.

### Advantages

- Easy to learn.
- Less code.
- Faster development.
- Flexible programming.

### Interview Tip

A common interview question is:

**Why is JavaScript dynamically typed?**

Answer:

Because variables are not bound to a single data type. A variable can hold different types of values during execution without requiring explicit type declarations.

---
