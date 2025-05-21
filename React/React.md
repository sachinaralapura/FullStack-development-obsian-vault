
- [[useState]]
- [[useContext]]
- [[useRef Hook]]
- [[useCallback Hook]]
- [[useMemo Hook]]
- [[Virtual Dom]]
- [[controlled and uncontrolled components]]
- [[Variable vs State]]
- [[Reconciliation]]
- [[HOC| Higher Order component]]


### **Basic Level (for Freshers and Juniors)**

1. **[[#What is React]]**

2. **[[#What are the features of React?]]**

3. **[[#**What is JSX?**]]**

4. **What is the virtual DOM and how does it work?**

5. **What are components in React?**

	- Functional vs Class components

6. **What are props in React?**

7. **[[#What is state in React?]]**

8. **How does the `setState` method work?**

9. [[controlled and uncontrolled components|**What are controlled and uncontrolled components?**]]

10. **How do you handle events in React?**


---

### **Intermediate Level**

1. **What is the difference between props and state?**

2. **What is the purpose of keys in React lists?**

3. **What is lifting state up in React?**

4. **What are React Hooks?**

    - useState, useEffect, useContext, etc.

5. **How does useEffect work?**

6. **What are custom hooks?**

7. **What is the Context API and when would you use it?**

8. **What is React Router and how do you implement routing in React?**

9. **How do you handle form submissions in React?**

10. **What is conditional rendering in React?**


---

###  **Advanced Level**

1. **What are Higher-Order Components (HOC)?**

2. **What is memoization in React?**

    - `React.memo`, `useMemo`, `useCallback`

3. **Explain reconciliation in React.**

4. **What are render props?**

5. **Explain the React Fiber architecture.**

6. **How would you optimize performance in a React app?**

7. **What are the differences between useEffect and useLayoutEffect?**

8. **What is server-side rendering (SSR) in React?**

9. **What are error boundaries in React?**

10. **How does React handle re-renders?**

---

###  **React with Ecosystem Tools**

1. **How do you style components in React?**

    - CSS Modules, Styled Components, Tailwind, etc.

2. **What is Redux and how does it work with React?**

3. **How does React Query (or SWR) help in data fetching?**

4. **How do you implement lazy loading in React?**

5. **Explain code splitting in React.**


---

### **Project/Scenario-Based Questions**

1. **Can you describe a React project you’ve worked on?**

2. **How did you manage state in your project?**

3. **How did you handle API integration in your project?**

4. **What challenges did you face while working with React, and how did you overcome them?**

5. **Have you used TypeScript with React? If yes, how do you type props and state?**

---
# What is React

ReactJS is a declarative, efficient, and flexible JavaScript library for building user interfaces (UIs) or UI components. It's maintained by Meta (formerly Facebook) and a large community of individual developers and companies

# What are the features of React?

- ### **Component-Based Architecture**
- ### **Virtual DOM**
- ### **JSX (JavaScript XML)**
- ### **Declarative Programming**
- ### Unidirectional Data Flow

# **What is JSX?**

JSX (JavaScript XML) is a syntax extension for JavaScript that allows you to write HTML-like structures directly within your JavaScript code.


# What is Props

Think of them as arguments you pass to a function, but in the context of React components, they are read-only values that allow parent components to control and configure their children.

# What is state in React?

In React, state is a mechanism that allows components to manage and update their own internal data over time. Unlike props, which are passed down from parent components and are read-only from the child's perspective, state is managed within a component and can be changed in response to user interactions, network requests, or other events. When a component's state changes, React re-renders the component and its children, updating the UI to reflect the new data