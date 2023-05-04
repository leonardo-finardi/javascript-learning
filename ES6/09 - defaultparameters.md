ES6 introduced default parameters, which allow you to specify default values for function parameters. If a parameter is not passed when the function is called, its default value is used instead. Here's an example:

```javascript
function greet(name = 'World') {
  console.log(`Hello, ${name}!`);
}

greet(); // output: 'Hello, World!'
greet('John'); // output: 'Hello, John!'
```

In this example, we're defining a function called greet with a default parameter of 'World' for the name parameter. If the name parameter is not passed when the function is called, its default value of 'World' is used instead. We're then calling the greet function twice, once without passing any arguments and once with the argument 'John'.

Here are some other key features of Default Parameters:

Default parameters can be any valid expression, not just simple values.
Default parameters are evaluated at the time of function execution, not at the time of function definition.
Default parameters can reference previously defined parameters in the function.

```javascript
function sum(a, b = a) {
  return a + b;
}

console.log(sum(2)); // output: 4
console.log(sum(2, 3)); // output: 5
```
In this example, we're defining a function called sum with two parameters, a and b, with a default value of a for b. If the b parameter is not passed when the function is called, its default value of a is used instead. We're then calling the sum function twice, once with one argument and once with two arguments.

Overall, Default Parameters are useful for providing fallback values for function parameters and simplifying function calls.