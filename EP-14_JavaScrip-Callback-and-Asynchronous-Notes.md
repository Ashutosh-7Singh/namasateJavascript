# ⏳ JavaScript Callbacks, Asynchronous Operations & Closures with Event Listeners

This document explains JavaScript callback functions, asynchronous behavior using `setTimeout`, closures in event listeners, and the importance of garbage collection.

---

## 🔁 Callback Functions

In JavaScript, functions are **first-class citizens**, which means they can be passed as arguments to other functions. A **callback function** is a function passed into another function to be executed later.

```js
function x(y) {
  console.log("x");
  y(); // callback
}

x(function y() {
  console.log("y");
});
```

> The function `y` is a **callback** because it is passed to `x` and called later within it.

---

## 🕒 Asynchronous JavaScript with `setTimeout`

JavaScript is a **synchronous single-threaded** language, meaning it executes one line at a time. However, using **Web APIs** like `setTimeout`, we can perform asynchronous operations.

```js
setTimeout(function () {
  console.log("timer");
}, 5000);
```

- `setTimeout` takes a **callback function** and a **delay (in ms)**.
- The callback is executed after the delay — allowing async behavior.

> 🧠 If JavaScript didn’t support first-class functions and callbacks, async operations like `setTimeout` wouldn't be possible.

---

## ⌛ "Time, tide, and JavaScript wait for none."

This quote signifies how `setTimeout` schedules code to run later regardless of what comes before it — non-blocking behavior.

---

## 🧠 Event Listeners and Callbacks

Event listeners are another use-case of callbacks.

```js
document.getElementById("clickMe").addEventListener("click", function () {
  console.log("Button Clicked");
});
```

- When the button is clicked, the callback is invoked.
- `addEventListener` internally stores the callback to call it on the event.

---

## 🔒 Closures with Event Listeners

Closures help retain access to variables even after the outer function has completed execution.

```js
function attachEventListner() {
  let count = 0;
  document.getElementById("clickMe").addEventListener("click", function () {
    console.log("Button Clicked", ++count);
  });
}
```

- Here, the inner callback **closes over** `count`, preserving it between clicks.
- This is useful for **data hiding and encapsulation**.

---

## ♻️ Garbage Collection & `removeEventListener`

### Why remove event listeners?

Event listeners hold references to their closure scope, preventing memory from being freed — even if nothing is using them anymore.

- **Memory Leak Risk**: Unremoved listeners keep variables in memory.
- **Performance**: Too many active listeners can slow down your app.

```js
const button = document.getElementById("clickMe");

function handleClick() {
  console.log("Clicked");
}

button.addEventListener("click", handleClick);

// Later, when not needed
button.removeEventListener("click", handleClick);
```

> Always clean up listeners when they’re no longer needed, especially in SPAs or dynamically generated elements.

---

## ✅ Summary

| Concept              | Description |
|----------------------|-------------|
| Callback Function    | A function passed into another function |
| setTimeout           | Schedules a function to run later (async) |
| Event Listener       | Executes a callback when an event occurs |
| Closure              | A function remembers variables from its scope |
| removeEventListener  | Helps with memory management and performance |

---