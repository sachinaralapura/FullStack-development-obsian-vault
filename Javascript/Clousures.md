**A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment).** This "enclosure" gives the inner function access to the outer function's variables even after the outer function has finished executing.

Ah, closures in JavaScript! They are a powerful and sometimes initially mind-bending concept, but once you grasp them, they become an indispensable tool in your JavaScript arsenal.

In simple terms, a closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). This "enclosure" gives the inner function access to the outer function's variables even after the outer function has finished executing.

Let's break down the key aspects:

### 1. Inner Functions and Outer Functions:

Closures arise when you define a function inside another function (the outer function). The inner function has access to the outer function's scope, including its variables, parameters, and even other inner functions.

JavaScript
```js

function outerFunction(outerVar) {
  let innerVar = 'Hello';

  function innerFunction() {
    console.log(outerVar); // Inner function accessing outerVar
    console.log(innerVar); // Inner function accessing its own var
  }

  return innerFunction; // Returning the inner function
}

const myInnerFunc = outerFunction('Hi from outer');
myInnerFunc(); // Output: Hi from outer
			   // Hello
```
In this example, innerFunction is defined inside outerFunction. When outerFunction is called, it creates its lexical environment, including outerVar and innerVar. It then returns innerFunction.

### 2. The Lexical Environment:

The crucial part is the lexical environment. When a function is created, it "remembers" its surrounding environment – where it was defined. This is different from the dynamic scope you might find in some other languages (where scope is based on where the function is called).

Even after outerFunction has finished executing and its execution context is popped off the call stack, the innerFunction (which is now stored in myInnerFunc) retains a reference to the lexical environment of outerFunction where it was originally defined.

### 3. Access to Outer Variables After Outer Function Execution:

This is the magic of closures. Because the inner function "closes over" the outer function's variables, it can still access and even modify them (if they are not constants) even after the outer function has completed.

Code snippet

```js
function counter() {
  let count = 0;

  return {
    increment: function() {
      count++;
    },
    decrement: function() {
      count--;
    },
    getCount: function() {
      return count;
    }
  };
}

const myCounter = counter();
myCounter.increment();
myCounter.increment();
console.log(myCounter.getCount()); // Output: 2
myCounter.decrement();
console.log(myCounter.getCount()); // Output: 1
```

Here, the counter function returns an object containing three inner functions (increment, decrement, and getCount). These inner functions form closures over the count variable from the counter function's scope. Even after counter finishes executing, these inner functions can still access and modify the count variable.

## Why are Closures Important?

Closures are a fundamental concept that enables several powerful patterns in JavaScript:

- **Data Encapsulation and Privacy**: By using closures, you can create private variables. In the counter example, the count variable is not directly accessible from outside the counter function. It can only be accessed and modified through the methods returned by the closure. This helps in preventing accidental modification of data.

- **Creating Functions with Memory**: Closures allow inner functions to "remember" the state of their outer environment across multiple invocations. This is essential for patterns like counters, state management, and creating specialized functions.

- **Currying and Partial Application**: Closures are often used in functional programming techniques like currying (transforming a function that takes multiple arguments into a sequence of functions that each take a single argument) and partial applications of an original function).

- **Module Pattern**: Closures are a key component of the module pattern in JavaScript, which helps in organizing code and preventing naming conflicts by creating self-contained units of functionality.

- **Iterators and Generators**: Closures play a role in implementing iterators and generators, allowing them to maintain state as they are iterated over.

#### Things to Keep in Mind:

- **Memory Usage**: Because the inner function retains a reference to the outer function's lexical environment, the variables in that environment are not garbage collected as long as the inner function exists. This can lead to increased memory usage if closures are not used carefully, especially in long-lived applications.

- **Accidental Binding:** Be mindful of variables in the outer scope that might be changed unexpectedly, as the closure will always refer to the current value of those variables.