Promises in ES6 provide a way to handle asynchronous operations in a more structured and predictable way. Promises allow you to chain operations and handle success and error cases separately.

Here's an example of how to use Promises in ES6:

```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    // perform asynchronous operation, such as an API call
    setTimeout(() => {
      const data = { message: 'Hello, World!' };
      if (data) {
        resolve(data);
      } else {
        reject(new Error('Failed to fetch data.'));
      }
    }, 1000);
  });
}

fetchData()
  .then((data) => {
    console.log(data.message); // outputs "Hello, World!"
  })
  .catch((error) => {
    console.error(error.message); // outputs "Failed to fetch data."
  });
```

In this example, we're defining a fetchData function that returns a new Promise. The Promise is resolved with some data if the asynchronous operation is successful or rejected with an error if it fails. We then call the fetchData function and chain the then and catch methods to handle success and error cases separately.

The then method is called if the Promise is resolved successfully. The function passed to then takes the resolved value as a parameter. In this example, we're logging the message property of the resolved data object.

The catch method is called if the Promise is rejected with an error. The function passed to catch takes the error object as a parameter. In this example, we're logging the error message to the console.

Overall, Promises in ES6 provide a powerful way to handle asynchronous operations in a more structured and predictable way. They allow you to write cleaner and more maintainable code that is easier to reason about.