Async/await is a new way to write asynchronous code in JavaScript introduced in ES6. It's built on top of Promises and provides a cleaner and more concise syntax for handling asynchronous operations. Async/await allows you to write asynchronous code that looks and behaves like synchronous code, making it easier to read and maintain.

Here's an example of how to use Async/await:

```javascript
async function fetchUsers() {
  const response = await fetch('https://jsonplaceholder.typicode.com/users');
  const data = await response.json();
  return data;
}

fetchUsers()
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

In this example, we're defining an async function called fetchUsers that uses the fetch API to retrieve data from an external API. We're then using the await keyword to wait for the response from the server and parse it as JSON data. Finally, we're returning the data from the function. We're then calling the fetchUsers function and using the .then() and .catch() methods to handle the returned data or any errors that occur.

Here are some other key features of Async/await:

An async function always returns a Promise.
The await keyword can only be used inside an async function.
Multiple await statements can be used sequentially to wait for multiple Promises to resolve.
Errors can be caught using a try/catch block.

```javascript
async function fetchUserById(id) {
  try {
    const response = await fetch(`https://jsonplaceholder.typicode.com/users/${id}`);
    const data = await response.json();
    return data;
  } catch (error) {
    console.error(error);
  }
}

fetchUserById(1)
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

In this example, we're defining an async function called fetchUserById that takes an id parameter and uses the fetch API to retrieve data for a specific user. We're using a try/catch block to catch any errors that occur during the asynchronous operation. We're then calling the fetchUserById function and using the .then() and .catch() methods to handle the returned data or any errors that occur.

Overall, Async/await is a powerful tool for writing asynchronous code in a cleaner and more readable way. It allows you to write asynchronous code that looks and behaves like synchronous code, making it easier to reason about and maintain.