Iterators and generators in ES6 provide a way to work with sequences of values in a more flexible and expressive way. Iterators are objects that provide a way to iterate over a sequence of values, while generators are functions that can be used to create iterators.

Here's an example of how to use an iterator in ES6:

```javascript
const numbers = [1, 2, 3, 4, 5];
const iterator = numbers[Symbol.iterator]();

console.log(iterator.next()); // outputs "{ value: 1, done: false }"
console.log(iterator.next()); // outputs "{ value: 2, done: false }"
console.log(iterator.next()); // outputs "{ value: 3, done: false }"
console.log(iterator.next()); // outputs "{ value: 4, done: false }"
console.log(iterator.next()); // outputs "{ value: 5, done: false }"
console.log(iterator.next()); // outputs "{ value: undefined, done: true }"
```

In this example, we're creating an iterator for an array of numbers using the Symbol.iterator method. We then call the next method on the iterator to iterate over the sequence of values. The next method returns an object with two properties: value and done. The value property contains the current value of the iteration, while the done property indicates whether the iteration is complete.

Here's an example of how to use a generator in ES6:

```javascript
function* fibonacci() {
  let a = 0;
  let b = 1;
  while (true) {
    yield a;
    [a, b] = [b, a + b];
  }
}

const iterator = fibonacci();
console.log(iterator.next()); // outputs "{ value: 0, done: false }"
console.log(iterator.next()); // outputs "{ value: 1, done: false }"
console.log(iterator.next()); // outputs "{ value: 1, done: false }"
console.log(iterator.next()); // outputs "{ value: 2, done: false }"
console.log(iterator.next()); // outputs "{ value: 3, done: false }"
```

In this example, we're defining a generator function called fibonacci that generates an infinite sequence of Fibonacci numbers. We're using the yield keyword to yield the current value of the sequence. We then create an iterator for the generator using the function call syntax with the * symbol. We then call the next method on the iterator to iterate over the sequence of values.

Overall, iterators and generators in ES6 provide a powerful way to work with sequences of values in a more flexible and expressive way. They allow you to write cleaner and more maintainable code that is easier to reason about.

More examples:

## Iterators 

```javascript
// Create a custom iterator for an object
const person = {
  name: 'Alice',
  age: 30,
  [Symbol.iterator]: function*() {
    for (let key in this) {
      yield `${key}: ${this[key]}`;
    }
  }
};

for (let property of person) {
  console.log(property); // outputs "name: Alice", "age: 30"
}

// Create a custom iterator for a string
const string = 'hello';
const iterator = string[Symbol.iterator]();

for (let char of iterator) {
  console.log(char); // outputs "h", "e", "l", "l", "o"
}
```

In the first example, we're defining a custom iterator for an object using a generator function. The generator yields a string for each property in the object. We then use a for...of loop to iterate over the object and log each property to the console.

In the second example, we're creating an iterator for a string using the Symbol.iterator method. We then use a for...of loop to iterate over the string and log each character to the console.

## Generators

```javascript
// Create a generator that generates the first n even numbers
function* evenNumbers(n) {
  let i = 0;
  while (i < n) {
    yield i * 2;
    i++;
  }
}

for (let num of evenNumbers(5)) {
  console.log(num); // outputs 0, 2, 4, 6, 8
}

// Create a generator that generates a random number between min and max
function* randomNumber(min, max) {
  while (true) {
    yield Math.floor(Math.random() * (max - min + 1) + min);
  }
}

const iterator = randomNumber(1, 10);
console.log(iterator.next().value); // outputs a random number between 1 and 10
console.log(iterator.next().value); // outputs a different random number between 1 and 10
```
In the first example, we're defining a generator function called evenNumbers that generates the first n even numbers. We're using a while loop and the yield keyword to generate each even number. We then use a for...of loop to iterate over the generator and log each even number to the console.

In the second example, we're defining a generator function called randomNumber that generates a random number between min and max. We're using a while loop and the yield keyword to generate a random number each time the generator is called. We then create an iterator for the generator and call the next method to generate a random number. We can continue to call the next method to generate more random numbers.