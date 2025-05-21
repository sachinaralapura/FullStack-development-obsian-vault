---
tags:
  - javascript
---
 These are performance optimization techniques used to control how often a function gets executed, especially in response to fast-occurring events like scrolling, typing, or resizing.

---
##  1. Debouncing

**Debouncing** ensures that a function is **only called once after a specified delay**—but only if the event doesn't happen again during that delay.

###  Use case:

You don't want to send an API call on every keystroke, but instead, wait for the user to stop typing for, say, 500ms.

### 🛠 How it works:

Every time the event is triggered, the timer resets. The function only executes if no more events happen during the delay.

### 🔤 Example:

```javascript
function debounce(func, delay) {
  let timeout;
  return function (...args) {
    clearTimeout(timeout);
    timeout = setTimeout(() => func.apply(this, args), delay);
  };
}
```

###  In React (input search example):

```jsx
import { useState, useEffect } from 'react';

function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const handler = setTimeout(() => setDebouncedValue(value), delay);
    return () => clearTimeout(handler);
  }, [value, delay]);

  return debouncedValue;
}
```

```jsx
function Search() {
  const [input, setInput] = useState('');
  const debouncedInput = useDebounce(input, 500);

  useEffect(() => {
    // API call happens only when debouncedInput changes
    console.log("Searching for:", debouncedInput);
  }, [debouncedInput]);

  return <input value={input} onChange={e => setInput(e.target.value)} />;
}
```

---

## ⚡ 2. Throttling

**Throttling** ensures a function is called **at most once every X milliseconds**, **no matter how many times the event occurs**.

###  Use case:

You want to limit how often a function is called while scrolling or resizing the window.

### 🛠 How it works:

Once the function is called, it won't be triggered again until the delay time has passed.

### 🔤 Example:

```javascript
function throttle(func, limit) {
  let lastCall = 0;
  return function (...args) {
    const now = Date.now();
    if (now - lastCall >= limit) {
      lastCall = now;
      func.apply(this, args);
    }
  };
}
```

###  In React (scroll example):

```jsx
useEffect(() => {
  const handleScroll = throttle(() => {
    console.log("Scroll position:", window.scrollY);
  }, 500);

  window.addEventListener('scroll', handleScroll);
  return () => window.removeEventListener('scroll', handleScroll);
}, []);
```

---

## Quick Comparison

|Feature|Debouncing|Throttling|
|---|---|---|
|Definition|Wait until user stops triggering|Call function at regular interval|
|Use case|Search box, form validation, resize|Scroll events, button spamming|
|Execution|Once after delay|Periodically during events|

---

If you want, I can help you install `lodash` and use its `debounce`/`throttle` functions too—they're super handy.

Let me know if you want to see both implemented together in a React component!