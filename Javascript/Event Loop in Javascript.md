The event loop in JavaScript! It's a fundamental concept that allows JavaScript to handle asynchronous operations in a non-blocking way, even though it's a single-threaded language. Think of it as the conductor of an orchestra, managing different tasks and ensuring everything runs smoothly without getting stuck.

**The Core Components:**

1. **The Call Stack:** This is like a stack of function calls. When you execute a JavaScript program, functions are pushed onto the stack when they are called and popped off when they return. JavaScript executes the topmost function on the stack. It's synchronous, meaning it processes one thing at a time.

2. **The Heap:** This is where objects (like those you create with `new`) are stored in memory. It's a less structured area compared to the call stack.

3. **The Event Queue (or Message Queue):** This is a queue of callback functions waiting to be executed. These callbacks are associated with asynchronous events (like a timer expiring, a user clicking a button, or a network request completing).

4. **The Event Loop:** This is the heart of the asynchronous magic. It constantly monitors the call stack and the event queue. If the call stack is empty, it takes the first callback from the event queue and pushes it onto the call stack for execution.

![[eventloop.png]]

There are two queue **Task Queue** and **Microtask Queue**. Javascript prioritizes **Microtask Queue**. 


**How it Works - The Cycle:**

1. **Initial Code Execution:** When your JavaScript code runs, the synchronous parts are executed directly and added to the call stack.
    
2. **Asynchronous Tasks:** When the JavaScript engine encounters an asynchronous operation (like `setTimeout`, `setInterval`, `fetch`, or event listeners), it doesn't block the main thread. Instead:
    
    - The **asynchronous operation is started** (e.g., the timer starts counting down, the network request is sent).
    - A **callback function** associated with that operation is registered.
    - The asynchronous operation and its management are often handled by **browser Web APIs** (for browser environments) or **Node.js APIs** (for Node.js environments).
3. **Callback Placement:** Once the asynchronous operation completes (e.g., the timer finishes, the network request returns), the **Web API or Node.js API pushes the associated callback function onto the Event Queue.**
    
4. **The Event Loop's Role:** The event loop continuously checks:
    
    - **Is the Call Stack empty?**
    - **Is there anything in the Event Queue?**
5. **Moving to the Stack:** If the call stack is empty and there are callbacks in the event queue, the event loop takes the **first callback from the queue** and **pushes it onto the call stack** for execution.
    
6. **Execution of Callback:** The callback function is now executed synchronously on the call stack. Once it completes, it's popped off.
    
7. **The Cycle Repeats:** This process continues indefinitely, allowing JavaScript to handle multiple asynchronous operations without freezing the user interface or blocking other tasks.

---
Task Queue (Macrotask Queue):

Priority: Lower priority. Tasks in this queue are processed after the call stack is empty and after the microtask queue has been completely emptied.
Timing: The event loop will execute at most one task from the task queue in each iteration of the event loop. After executing a task, the event loop will always check and process the entire microtask queue before picking up the next task from the task queue.

Types of Tasks: Primarily handles callbacks from:
- setTimeout and setInterval
- DOM events (e.g., click, mousemove)
- Network requests (fetch, XMLHttpRequest callbacks)
- setImmediate (in Node.js)
- I/O operations

Microtask Queue:

Priority: Higher priority. Microtasks are executed immediately after the currently executing script finishes, and importantly, before the event loop proceeds to the next task from the task queue or before rendering. The event loop will keep processing microtasks until this queue is empty, even if new microtasks are added during this process.

Timing: All microtasks in the queue are processed one after another as long as the call stack is empty, before the event loop moves to the next macrotask.

Types of Tasks: Primarily handles callbacks from:
- Promises (.then(), .catch(), .finally())
- MutationObserver API (for observing changes in the DOM)
- queueMicrotask() API

