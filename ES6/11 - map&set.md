## Map

The Map object is a data structure introduced in ES6 that allows you to store key-value pairs where both the key and value can be of any type. Map is similar to an object in JavaScript, but with a few key differences:

Keys in a Map can be of any type, including objects and functions.
A Map preserves the order of its elements, whereas an object does not.
A Map can have a size property that tells you how many key-value pairs it contains.
Here's an example of how to use Map:

```javascript
const myMap = new Map();

myMap.set('key1', 'value1');
myMap.set('key2', 'value2');

console.log(myMap.get('key1')); // output: 'value1'
console.log(myMap.size); // output: 2

```
In this example, we're creating a new Map object called myMap and using the set method to add key-value pairs to it. We're then using the get method to retrieve the value associated with a specific key, and the size property to get the number of key-value pairs in the Map.

## Set

The Set object is another data structure introduced in ES6 that allows you to store unique values of any type, including primitive values and object references. Set is similar to an array in JavaScript, but with a few key differences:

A Set can only contain unique values. If you try to add a duplicate value, it will be ignored.
A Set preserves the order of its elements, similar to an array.
A Set has a size property that tells you how many elements it contains.
Here's an example of how to use Set:

```javascript
const mySet = new Set();

mySet.add('value1');
mySet.add('value2');
mySet.add('value1');

console.log(mySet.size); // output: 2
```

In this example, we're creating a new Set object called mySet and using the add method to add values to it. We're then adding a duplicate value, but since Set can only contain unique values, it is ignored. Finally, we're using the size property to get the number of elements in the Set.

## WeakMap/WeakSet

The WeakMap and WeakSet objects are similar to Map and Set, respectively, but with one key difference: they allow their keys to be garbage collected when they are no longer referenced anywhere else in the program. This makes them useful for cases where you want to associate metadata with an object, but don't want to prevent the object from being garbage collected.

Here's an example of how to use WeakMap:

```javascript
const myWeakMap = new WeakMap();

const obj1 = {};
const obj2 = {};

myWeakMap.set(obj1, 'value1');
myWeakMap.set(obj2, 'value2');

console.log(myWeakMap.get(obj1)); // output: 'value1'

obj1 = null;

console.log(myWeakMap.get(obj1)); // output: undefined
```

In this example, we're creating a new WeakMap object called myWeakMap and using the set method to associate metadata with two objects, obj1 and obj2. We're then retrieving the metadata associated with obj1 using the get method. Finally, we're setting obj1 to