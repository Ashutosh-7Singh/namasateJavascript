# 📘 JavaScript Functions - A Complete Reference

This document explains different types of functions in JavaScript with clear definitions and examples.

---

## 📌 Function Statement / Declaration

A function statement (also called **function declaration**) defines a named function in the global scope.

```js
function a() {
    console.log("a called");
}

a(); // ✅ Works: Outputs "a called"
```

> ✅ Function declarations are hoisted. So you can call them before they're defined.

---

## 📌 Function Expression

A function can also be assigned to a variable. This is called a **function expression**.

```js
var b = function () {
    console.log("b called");
};

b(); // ✅ Works: Outputs "b called"
```

> ❌ Function expressions are **not hoisted**, so calling `b()` before its definition will throw an error.

---

## 📌 Anonymous Function

An **anonymous function** is a function without a name. It cannot be used as a standalone function declaration.

```js
// ❌ Invalid on its own
// function () {
//     console.log("This will throw an error");
// }

// ✅ Used as a value (e.g., in function expressions or callbacks)
var greet = function () {
    console.log("Hello!");
};
```

---

## 📌 Named Function Expression

A **named function expression** is when a function expression has a name.

```js
var c = function xyz() {
    console.log("xyz called");
};

c();    // ✅ Works
xyz();  // ❌ Error: xyz is not defined in the global scope
```

> ⚠️ The name `xyz` is only available inside the function body, not in the outer/global scope.

---

## 📌 Parameters vs Arguments

- **Parameters** are placeholders used when defining a function.
- **Arguments** are the actual values passed when calling the function.

```js
function greet(name) {  // name is a parameter
    console.log("Hello, " + name);
}

greet("Ashutosh");  // "Ashutosh" is the argument
```

---

## 📌 First-Class Functions

JavaScript treats functions as **first-class citizens**, which means:

- Functions can be passed as arguments to other functions.
- Functions can be returned from other functions.
- Functions can be assigned to variables.

```js
// Passing a function as an argument
function executeCallback(callback) {
    callback();
}

executeCallback(function () {
    console.log("Callback executed!");
});

// Returning a function from another function
function outer() {
    return function inner() {
        console.log("Inner function returned");
    };
}

const result = outer();
result(); // Outputs: Inner function returned
```

---

## 📌 Summary

| Concept                  | Description                                                           | Example                                  |
|--------------------------|------------------------------------------------------------------------|------------------------------------------|
| Function Declaration     | Function defined with `function` keyword                              | `function a() {}`                        |
| Function Expression      | Function assigned to a variable                                        | `const b = function() {}`               |
| Anonymous Function       | Function with no name                                                  | `() => {}` or inside `setTimeout`       |
| Named Function Expression| Function expression with a name                                        | `const c = function xyz() {}`           |
| Parameters & Arguments   | Inputs to a function definition vs invocation                          | `function(x)` vs `func(5)`              |
| First-Class Functions    | Functions can be passed and returned like any other variable           | `return function() {}`                  |

---

## 🔥 Extra Tip: Arrow Functions

Arrow functions are shorthand for function expressions.

```js
const greet = () => {
    console.log("Hi from arrow function!");
};
```