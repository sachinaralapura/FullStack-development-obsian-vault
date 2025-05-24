 Redux enables you to maintain a single centralized store that manages the state of your entire application. All components in your application can access this store and update or retrieve data from it as needed.

**The key components that enable this centralized approach to state management are:**

1. Store
2. Actions
3. Dispatch
4. Reducers

---
### STORE

The Redux store is like a giant container that holds all the data for your application.
Think of the store as a box with different compartments for different data types. You can store any data you want in these compartments, and it can hold various kinds of data, such as strings, numbers, arrays, objects, and even functions.

Also, the store is the single **source of truth** for your application's state. This means that any component in your application can access it to retrieve and update data.

---
## ACTIONS

An action is an **==object==** that describes what changes need to be made to the state of your application. It sends data from your application to the Redux store and serves as the only way to update the store.

- An action must have a "==type==" property describing the action being performed. This "type" property is typically defined as a string constant to ensure consistency and avoid typos.
- An action can have "==payload==". The "payload" property represents the data that provides additional information about the action being performed. For example, if an action type is `ADD_TASK`, the payload might be an object containing a new task item's "id", "text", and "completed status".

```js
{
  type: 'ADD_TASK',
  payload: {
    id: 1,
    text: 'Buy groceries',
    completed: false
  }
}
```

- #### Action creators
To create actions, we use action creators. Action creators are functions that create and return action objects.

Example of an action creator that takes in a task's text and returns an action object to add the task to the Redux store:

```javascript
function addTask(taskText) {
  return {
    type: 'ADD_TASK',
    payload: {
      id: 1,
      text: taskText,
      completed: false
    }
  }
}
```

---

## DISPATCH

In Redux, dispatch is a function provided by the store that allows you to send an action to update the state of your application. When you call `dispatch`, the store runs an action through all of the available reducers, which in turn update the state accordingly.

You can think of `dispatch` as a mail carrier who delivers mail to different departments in a large company. Just like how the mail carrier delivers mail to different departments, `dispatch` delivers actions to various reducers in your Redux store. Each reducer is like a department in the company that processes the mail and updates its own part of the company's data.

---
## ACTIONS

In Redux, a reducer is a **function** that takes in the ==**current state**== of an application and an **==action==** as arguments, and returns a ==new state== based on the action.

```javascript
const initialState = {
  count: 0
};

function counterReducer(state = initialState, action) {
  switch(action.type) {
    case 'INCREMENT':
      return { ...state, count: state.count + 1 }; // return new State
    case 'DECREMENT':
      return { ...state, count: state.count - 1 }; // return new state
    default:
      return state;
  }
}
```

---

![[reduxdataflow.gif]]