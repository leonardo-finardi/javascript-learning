Arrow functions are a new syntax for creating functions in JavaScript introduced in ES6. They are often used as a shorthand for writing functions, making code shorter and more concise.

Here's the basic syntax for an arrow function:

```javascript
// A function that takes two parameters and returns their sum
const sum = (a, b) => a + b;
```

The function above takes two parameters a and b, and returns their sum using the arrow function syntax =>. The parentheses around the parameters are optional if there's only one parameter, and the curly braces are optional if there's only one statement in the function body.

Here are a few more examples of arrow functions:

```javascript
// A function that returns the square of a number
const square = x => x * x;

// A function that returns true if a number is even, false otherwise
const isEven = num => num % 2 === 0;

// A function that returns a greeting message for a given name
const greet = name => `Hello, ${name}!`;

```
One of the advantages of arrow functions is that they automatically bind the value of this to the value of the surrounding lexical context. This means that you don't need to use the bind, call, or apply methods to bind this to the correct value.

```javascript
// An object with a method that uses this inside an arrow function
const obj = {
  name: 'Alice',
  greet: () => {
    console.log(`Hello, my name is ${this.name}`); // 'this' refers to the global object, not the object 'obj'
  }
};

obj.greet(); // 'Hello, my name is undefined'
```
In the example above, the this keyword inside the arrow function greet refers to the global object, not the object obj. To fix this, you can use a regular function expression instead of an arrow function.

```javascript
// An object with a method that uses this inside a regular function expression
const obj = {
  name: 'Alice',
  greet: function() {
    console.log(`Hello, my name is ${this.name}`); // 'this' refers to the object 'obj'
  }
};

obj.greet(); // 'Hello, my name is Alice'
```