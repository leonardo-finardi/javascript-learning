## Spread Operator

The spread operator is denoted by three dots (...) and can be used to "spread" the elements of an iterable (e.g. an array or a string) into individual elements. Here are a few examples:

```javascript
const myArray = [1, 2, 3];
const newArray = [...myArray, 4, 5, 6];

console.log(newArray); // output: [1, 2, 3, 4, 5, 6]
```

In this example, we're using the spread operator to spread the elements of myArray into individual elements of a new array. We're then adding some additional elements to the new array and logging the new array to the console.

```javascript
const myString = 'hello';
const newArray = [...myString];

console.log(newArray); // output: ['h', 'e', 'l', 'l', 'o']
```

In this example, we're using the spread operator to spread the characters of myString into individual elements of a new array. We're then logging the new array to the console.

```javascript
const myObject = { foo: 1, bar: 2 };
const newObj = { ...myObject, baz: 3 };

console.log(newObj); // output: { foo: 1, bar: 2, baz: 3 }
```

In this example, we're using the spread operator to spread the properties of myObject into a new object. We're then adding a new property to the new object and logging the new object to the console.

## Rest Operator

The rest operator is also denoted by three dots (...) and can be used to "gather" the remaining arguments into an array. Here's an example:

```javascript
function myFunction(arg1, arg2, ...args) {
  console.log(arg1); // output: 1
  console.log(arg2); // output: 2
  console.log(args); // output: [3, 4, 5]
}

myFunction(1, 2, 3, 4, 5);
```
In this example, we're defining a function called myFunction with two regular arguments (arg1 and arg2) and a rest parameter (args). When we call myFunction with five arguments, the first two arguments are assigned to arg1 and arg2, and the remaining arguments are gathered into an array called args. We then log the values of arg1, arg2, and args to the console.

Together, these operators can be very powerful for working with arrays, objects, and functions in JavaScript.
