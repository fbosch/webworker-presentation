---
marp: true
theme: uncover
title: Web Workers
description: Multi-threading in JavaScript
paginate: true
_paginate: false
---

![bg](#222)
![](#fff)

# <!--fit--> ⚙️ Web Workers

### <!--fit--> Multi-threading in JavaScript

---

# Prerequisite

- JavaScript is a single-threaded language with asynchronous capabilities
- Web Workers are a part of the [Living Standard](https://html.spec.whatwg.org/multipage/workers.html#workers)
- ... they have existed for quite a while but they are still not very used by developers

---

# Benefits of Workers

Running computationally intensive code in a web worker can help you prevent a laggy or completely unresponsive user experience

![](./assets/dead.svg)

---

# Communication

![](./assets/worker-flow.svg)

---

# API

```js
// worker.js
self.addEventListener("message", (event) => {
  if (event.data === "foo") {
    self.postMessage("bar");
  }
});
```

```js
// main.js
const worker = new Worker("./worker.js");

worker.onmessage = (event) => {
  console.assert(event.data === "bar");
};

worker.postMessage("foo");
```
