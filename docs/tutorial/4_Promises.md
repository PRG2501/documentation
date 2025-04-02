# Promises in JavaScript

A Promise is like a special container that holds a value that might not be available right away. Think of it like ordering food at a restaurant - you place your order (start an operation) and get a receipt (Promise) that says your food will be ready soon. The food isn't ready immediately, but you have a way to know when it will be.

## Basic Promise Structure

A Promise can be in one of three states:

- **Pending**: The initial state (like waiting for your food)
- **Fulfilled**: The operation completed successfully (your food is ready!)
- **Rejected**: The operation failed (sorry, we're out of that dish)

## Using Promises with .then()

The most basic way to use a Promise is with the `.then()` method. Here's a simple example:

```javascript
// Create a simple Promise
const myPromise = new Promise((resolve, reject) => {
  // This is where you do something that takes time
  setTimeout(() => {
    resolve("Hello!"); // Success!
    // or
    // reject("Oops!"); // Error!
  }, 1000);
});

// Use the Promise
myPromise.then((result) => {
  console.log(result); // Will print "Hello!" after 1 second
});
```

## Real-World Example

Here's a practical example using the icanhazdadjoke API to fetch a random dad joke:

```javascript
// Fetch a dad joke from the API
fetch("https://icanhazdadjoke.com/", {
  headers: {
    Accept: "text/plain", // we will explain what headers are in a later class
  },
})
  .then((response) => response.text())
  .then((joke) => {
    console.log("Here's your dad joke:", joke);
  });
```

### Understanding Chained .then() Calls

In the example above, we use two `.then()` calls in a chain. Here's how it works:

1. The first `.then()` receives the response from the server:

   ```javascript
   .then((response) => response.text())
   ```

   - This gets the raw response from the server
   - `response.text()` converts the response into plain text
   - This returns a new Promise with the text content

2. The second `.then()` receives the text content:
   ```javascript
   .then((joke) => {
     console.log("Here's your dad joke:", joke);
   });
   ```
   - This receives the text content from the previous step
   - Now we can use the joke text as we want

Each `.then()` call:

- Waits for the previous Promise to complete
- Receives the result from the previous step
- Can return a new value (which becomes a new Promise)
- Or just performs an action without returning anything

## Key Points to Remember

1. Promises help you handle operations that take time to complete
2. `.then()` is used to handle the successful result of a Promise
3. The code inside `.then()` only runs after the Promise is fulfilled
4. You can chain multiple `.then()` calls together

## Common Use Cases

- Loading data from a server
- Reading files
- Processing images
- Any operation that might take some time to complete

Remember: Promises make it easier to work with asynchronous code (code that doesn't run immediately) in a more organized way.
