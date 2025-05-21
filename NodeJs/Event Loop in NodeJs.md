---
tags:
  - nodejs
---

At its core, the Node.js Event Loop is a **single-threaded, non-blocking I/O model** that allows Node.js to perform asynchronous operations. It's the mechanism that enables Node.js to handle many concurrent operations without blocking the main thread.

#### Why a Single Thread?

A common misconception is that Node.js is entirely single-threaded. While the _JavaScript execution_ is single-threaded (meaning your application code runs on one thread), Node.js uses a powerful library called **libuv** (written in C++) which provides the asynchronous I/O primitives. Libuv, in turn, uses a thread pool for certain I/O operations that are inherently blocking at the operating system level.

So, the single thread handles your JavaScript code, the event loop, and the queue of callbacks, while libuv manages the heavy lifting of I/O operations in the background, notifying the event loop when they are complete.

#### Simplified Flow:

1. Node.js starts, runs your synchronous code.
2. Any asynchronous operations (like `fs.readFile()`, `http.get()`, `setTimeout()`) are offloaded to libuv.
3. Their associated callbacks are placed in the appropriate queues.
4. Once the synchronous code finishes, the Event Loop begins its cycle through the phases.
5. It checks queues for ready callbacks and executes them.
6. It continuously repeats this cycle, processing events and executing callbacks as they become available.