## Proxies

A proxy is a new feature introduced in ES6 that allows you to intercept and customize operations performed on an object. Proxies enable you to define custom behavior for fundamental operations on an object such as reading and writing properties, calling methods, and accessing the object's prototype.

Here's an example of how to use Proxy:

```javascript
const myObject = { foo: 'bar' };

const myProxy = new Proxy(myObject, {
  get(target, prop) {
    console.log(`Getting ${prop}`);
    return target[prop];
  },

  set(target, prop, value) {
    console.log(`Setting ${prop} to ${value}`);
    target[prop] = value;
  }
});

console.log(myProxy.foo); // output: 'Getting foo' followed by 'bar'
myProxy.foo = 'baz'; // output: 'Setting foo to baz'
console.log(myProxy.foo); // output: 'Getting foo' followed by 'baz'
```

In this example, we're creating a new object called myObject and a Proxy object called myProxy. We're then intercepting and customizing the behavior of the get and set operations using the Proxy constructor's second argument. We're logging a message to the console indicating which operation is being performed, and then either returning the property value or setting the property value on the target object.

Reflect:

The Reflect object is a new built-in object introduced in ES6 that provides methods for performing meta-operations on objects, such as creating new objects, defining properties, and invoking methods. The Reflect methods mirror the functionality of the corresponding methods on the Object and Function objects, but with a few key differences:

The Reflect methods are designed to be used as functions and are not part of any object prototype.
The Reflect methods have a consistent and predictable API that makes it easier to work with them in a functional programming style.
Here's an example of how to use Reflect:

```javascript
const myObject = { foo: 'bar' };

const myProxy = new Proxy(myObject, {
  get(target, prop) {
    console.log(`Getting ${prop}`);
    return Reflect.get(target, prop);
  },

  set(target, prop, value) {
    console.log(`Setting ${prop} to ${value}`);
    return Reflect.set(target, prop, value);
  }
});

console.log(myProxy.foo); // output: 'Getting foo' followed by 'bar'
myProxy.foo = 'baz'; // output: 'Setting foo to baz'
console.log(myProxy.foo); // output: 'Getting foo' followed by 'baz'
```

In this example, we're using Reflect.get and Reflect.set to perform the get and set operations on the target object. The Reflect methods provide a consistent and predictable API for working with objects in a functional programming style.