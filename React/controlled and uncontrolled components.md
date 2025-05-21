In React, **controlled** and **uncontrolled** components are two different ways of handling form elements (like `<input>`, `<textarea>`, `<select>`). The key difference lies in where the source of truth for the form's data resides.

**Controlled Components:**

- **Source of Truth: React State:** In a controlled component, the value of the form element is directly tied to and controlled by the component's state.
- **Event Handling:** You attach event handlers (like `onChange`) to the form elements. These handlers update the component's state based on user input.
    
- **Data Flow:** The data flows from the state to the form element. When the user types, the state is updated, and React re-renders the component, updating the form element's value to reflect the new state.
    
- **Programmatic Control:** Because the state controls the value, you have complete programmatic control over the form element.3 You can easily validate input, format it, or conditionally disable/enable elements based on the state.
    

**Example (Controlled Input):**

JavaScript

```js
import React, { useState } from 'react';

function ControlledInput() {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (event) => {
    setInputValue(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    console.log('Submitted value:', inputValue);
    // You can now use the inputValue for further processing
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Controlled Input:
        <input
          type="text"
          value={inputValue} // Value is bound to the state
          onChange={handleChange} // Updates the state on every input change
        />
      </label>
      <button type="submit">Submit</button>
      <p>Current value: {inputValue}</p>
    </form>
  );
}

export default ControlledInput;
```

**Uncontrolled Components:**

- **Source of Truth: The DOM:** In an uncontrolled component, the form element's value is stored and managed by the DOM itself, just like traditional HTML forms.4

- **Refs for Accessing Values:** To access the value of an uncontrolled component, you typically use a `ref` to get a direct reference to the DOM element.
- **Less React Involvement:** React is less involved in the real-time updates of the form element's value. You generally access the value only when you need it (e.g., on form submission).

**Example (Uncontrolled Input):**

JavaScript

```js
import React, { useRef } from 'react';

function UncontrolledInput() {
  const inputRef = useRef(null);

  const handleSubmit = (event) => {
    event.preventDefault();
    console.log('Submitted value:', inputRef.current.value); // Access the DOM element's value using the ref
    // You can now use inputRef.current.value for further processing
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Uncontrolled Input:
        <input
          type="text"
          ref={inputRef} // Attach a ref to the input element
        />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default UncontrolledInput;
```

**When to Use Which:**

- **Controlled Components:**
    
    - **Recommended for most cases.**
    - When you need to implement input validation, formatting, or any logic that depends on the input value as the user types.
    - When you need to programmatically control the value of the input element.
    - When the form data needs to be stored and managed by your React component's state.
    - Provides a more "React-like" and predictable way to handle forms.5
        
- **Uncontrolled Components:**
    
    - Can be simpler for very basic forms where you only need to get the values on submit and don't need real-time control or validation.
    - Sometimes useful when integrating with third-party DOM libraries.
    - Might lead to slightly less code for very simple forms, but can become harder to manage for more complex scenarios.

**Key Differences Summarized:**

|   |   |   |
|---|---|---|
|**Feature**|**Controlled Components**|**Uncontrolled Components**|
|**Source of Truth**|React State|The DOM|
|**Value Binding**|`value` prop linked to state|No direct value binding|
|**Accessing Value**|Directly from state|Using `refs` to access DOM element|
|**Real-time Control**|Full programmatic control|Limited real-time control|
|**Complexity**|Can be slightly more verbose|Can be simpler for basic forms|
|**React Paradigm**|More aligned with React principles|More like traditional HTML forms|
