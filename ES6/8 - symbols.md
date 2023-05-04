A symbol is a new primitive data type introduced in ES6. A symbol is an immutable and unique value that can be used as an identifier for object properties. Here's an example:

```javascript
const mySymbol = Symbol('mySymbol');
const myObject = {};

myObject[mySymbol] = 'foo';

console.log(myObject[mySymbol]); // output: 'foo'

```

In this example, we're defining a new symbol called mySymbol with the description "mySymbol". We're then creating a new empty object called myObject and setting a property on it using the symbol as the key. We're then logging the value of the property to the console by using the symbol as the key.

The Symbol() function can be called with an optional description parameter which can be used for debugging and displaying the symbol. Two symbols created with the same description are not equal to each other.

Here are some other key features of Symbols:

Symbols are unique, so two symbols created with the same description are not equal to each other.
Symbols can be used as keys for object properties, but they are not enumerable in for...in loops or Object.keys() methods.
Symbols can be used to define "hidden" properties on objects that cannot be accessed or overwritten using regular object property accessors.

```javascript
const mySymbol = Symbol('mySymbol');
const myObject = {
  foo: 'bar',
  [mySymbol]: 'baz'
};

console.log(Object.keys(myObject)); // output: ['foo']
console.log(myObject[mySymbol]); // output: 'baz'

for (const key in myObject) {
  console.log(key); // output: 'foo'
}

myObject[mySymbol] = 'qux';
console.log(myObject[mySymbol]); // output: 'qux'

Object.defineProperty(myObject, mySymbol, { value: 'quux' });
console.log(myObject[mySymbol]); // output: 'qux'
```

In this example, we're creating a new symbol called mySymbol with the description "mySymbol". We're then creating a new object called myObject and setting two properties on it, one using a regular string key (foo) and one using the symbol as the key. We're then logging the keys of the object to the console using Object.keys() and a for...in loop. We're also logging the value of the symbol property using the symbol as the key. We're then trying to overwrite the symbol property using regular object property accessors, but we can't. Finally, we're defining a new value for the symbol property using Object.defineProperty().

Overall, Symbols are useful for creating unique identifiers that cannot be overwritten, as well as for creating "hidden" properties on objects.