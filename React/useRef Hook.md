---
tags:
  - reactjs
---
`useRef` is a React Hook that gives you a **mutable container** whose `.current` property **persists across renders**. It’s often used to:
1. Access and interact with **DOM elements**.
2. Store **mutable values** that **don’t cause re-renders** when changed.
3. Hold **any value** you want to survive between renders.

---

### Syntax:
```tsx
const myRef = useRef(initialValue);
```

---

### Use Case 1: Accessing a DOM Element

```tsx
import { useRef, useEffect } from "react";

function FocusInput() {
  const inputRef = useRef<HTMLInputElement>(null);

  useEffect(() => {
    inputRef.current?.focus(); // Auto-focus input on mount
  }, []);

  return <input ref={inputRef} type="text" />;
}
```

---

###  Use Case 2: Storing a Value Without Re-rendering

```tsx
import { useRef, useState, useEffect } from "react";

function Timer() {
  const [seconds, setSeconds] = useState(0);
  const intervalRef = useRef<NodeJS.Timeout | null>(null);

  useEffect(() => {
    intervalRef.current = setInterval(() => {
      setSeconds(s => s + 1);
    }, 1000);

    return () => clearInterval(intervalRef.current!); // clear on unmount
  }, []);

  return <p>Timer: {seconds}s</p>;
}
```

---

###  Use Case 3: Previous Value Tracking

```tsx
function Counter() {
  const [count, setCount] = useState(0);
  const prevCount = useRef<number>(0);

  useEffect(() => {
    prevCount.current = count;
  }, [count]);

  return (
    <>
      <p>Current: {count}</p>
      <p>Previous: {prevCount.current}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </>
  );
}
```

---

### Summary:
| `useRef` Is Used For...   | ✅ Does it cause re-render? |
| ------------------------- | -------------------------- |
| Referencing DOM elements  | ❌ No                       |
| Storing persistent values | ❌ No                       |
| Tracking previous values  | ❌ No                       |
