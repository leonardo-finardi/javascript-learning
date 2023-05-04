Destructuring is a new feature introduced in ES6 that allows you to extract values from objects or arrays and assign them to variables in a more concise way. Here's an example of destructuring an array:

```javascript
const numbers = [1, 2, 3, 4, 5];
const [first, second, , fourth] = numbers;
console.log(first, second, fourth); // outputs "1 2 4"
```

In this example, we're destructuring the numbers array into four variables using square brackets. We're assigning the first value to first, the second value to second, skipping the third value (using a comma without a variable name), and assigning the fourth value to fourth.

Destructuring also works with objects. Here's an example:

```javascript
const person = {
  name: 'John',
  age: 30,
  occupation: 'Developer'
};
const {name, age} = person;
console.log(name, age); // outputs "John 30"
```

In this example, we're destructuring the person object into two variables using curly braces. We're assigning the value of the name property to a name variable and the value of the age property to an age variable.

Destructuring can also be used in function parameters to extract values from objects or arrays. Here's an example:

```javascript
function printNameAndAge({name, age}) {
  console.log(`Name: ${name}, Age: ${age}`);
}

const person = {
  name: 'John',
  age: 30,
  occupation: 'Developer'
};

printNameAndAge(person); // outputs "Name: John, Age: 30"
```

In this example, we're defining a function that takes an object parameter and destructures the name and age properties into local variables. We're then logging the name and age values.

Overall, destructuring in ES6 allows for more concise and readable code when working with objects and arrays. It can help simplify assignments and function parameters and make code easier to understand.