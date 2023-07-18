Async functions in JavaScript provide a convenient way to write asynchronous code using Promises. They allow you to write asynchronous code that looks like synchronous code, making it easier to handle asynchronous operations and avoid callback hell. Here's an example of an async function in JavaScript:

```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error(error);
    throw new Error('Failed to fetch data');
  }
}

// Using the async function
fetchData()
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

In this example:

1. The `fetchData` function is declared as an async function.
2. Inside the function, we use the `await` keyword to wait for promises to resolve.
3. We make an asynchronous HTTP request using the `fetch` function, which returns a Promise that resolves to the response.
4. We use `await response.json()` to asynchronously parse the response as JSON, again returning a Promise that resolves to the parsed data.
5. The function either returns the data or throws an error if there's a problem.
6. When using the async function, we can handle the result using `.then()` and handle errors with `.catch()`.

Async functions make it easier to write asynchronous code that's more readable and maintainable by leveraging the power of Promises and `await` keyword for asynchronous operations.