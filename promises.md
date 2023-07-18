Promises in JavaScript are objects that represent the eventual completion or failure of an asynchronous operation. They provide a more structured way to handle asynchronous code compared to traditional callbacks. Here are some examples of using promises in JavaScript:

1. Basic Promise example:
```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = 'Fetched data';
      resolve(data); // Resolve the promise with the data
      // reject(new Error('Failed to fetch data')); // Reject the promise with an error
    }, 2000);
  });
}

// Using the promise
fetchData()
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

In this example, we create a Promise using the `Promise` constructor. Inside the executor function, we perform an asynchronous operation (e.g., fetching data) and then either call `resolve` with the result or `reject` with an error. The promise is then consumed using `.then()` to handle the resolved value and `.catch()` to handle any errors.

2. Promise chaining:
```javascript
function getData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = 'Data';
      resolve(data);
    }, 2000);
  });
}

function processData(data) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const processedData = data.toUpperCase();
      resolve(processedData);
      // reject(new Error('Failed to process data'));
    }, 2000);
  });
}

getData()
  .then((data) => processData(data))
  .then((processedData) => console.log(processedData))
  .catch((error) => console.error(error));
```

In this example, we have two functions: `getData()` and `processData()`. Each function returns a promise. We can chain these promises together using `.then()` to perform sequential asynchronous operations.

3. Promise .all():
```javascript
const fetchUser = new Promise((resolve, reject) => {
  setTimeout(() => {
    const user = { name: 'John', age: 30 };
    resolve(user);
  }, 2000);
});

const fetchPosts = new Promise((resolve, reject) => {
  setTimeout(() => {
    const posts = ['Post 1', 'Post 2', 'Post 3'];
    resolve(posts);
  }, 1500);
});

Promise.all([fetchUser, fetchPosts])
  .then(([user, posts]) => {
    console.log(user);
    console.log(posts);
  })
  .catch((error) => console.error(error));
```

In this example, we have two separate promises, `fetchUser` and `fetchPosts`, which simulate fetching user data and post data asynchronously. `Promise.all()` takes an array of promises and returns a new promise that resolves when all promises in the array have resolved. The resolved values of the individual promises are available as an array in the `.then()` callback.

Promises provide a more elegant way to handle asynchronous operations, making code more readable and maintainable by allowing you to chain operations, handle errors, and coordinate multiple asynchronous tasks.