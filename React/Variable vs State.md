## Normal JavaScript Variable:

- Scope: Its scope is determined by where it's declared (e.g., within a function, block, or globally).

- Mutability: You can directly change the value of a normal variable using standard assignment (=).
 
 - Rendering: Modifying a normal variable does not automatically trigger a re-render of the React component in which it's defined. The UI will only update if the component happens to re-render for some other reason (e.g., a parent component re-renders).

- Persistence: The value of a normal variable within a functional component is generally lost between renders. Each time the component function is executed, the variable is re-initialized.

## React State Variable (created using useState):

- Scope: The state variable is scoped to the specific component in which it's created.

- Mutability: You should not directly modify a state variable. Instead, you must use the state setter function provided by useState (e.g., setCount, setName).

- Rendering: Calling the state setter function triggers a re-render of the React component. This is the fundamental mechanism by which changes in data are reflected in the UI. React compares the previous and new Virtual DOM and updates the actual DOM efficiently.

- Persistence: React preserves the state variable's value across re-renders of the component. This allows components to maintain and update their own internal data over time, making them interactive.