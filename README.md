### Handling Asynchronous Operations in JavaScript

JavaScript provides several ways to handle asynchronous operations, including callbacks, promises, and async/await. Below is an explanation of each approach:

#### 1. Callbacks
A callback is a function passed as an argument to another function, which is then executed after the completion of an asynchronous operation.

**Example:**
```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback('Data fetched');
  }, 1000);
}

fetchData((message) => {
  console.log(message); // Output after 1 second: Data fetched
});
```

**Pros:**
- Simple and straightforward for small operations.

**Cons:**
- Can lead to "callback hell" or "pyramid of doom" when chaining multiple asynchronous operations.

#### 2. Promises
Promises provide a cleaner way to handle asynchronous operations by representing a value that may be available now, or in the future, or never.

**Example:**
```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve('Data fetched');
    }, 1000);
  });
}

fetchData()
  .then((message) => {
    console.log(message); // Output after 1 second: Data fetched
  })
  .catch((error) => {
    console.error(error);
  });
```

**Pros:**
- Avoids callback hell.
- Easier to chain multiple asynchronous operations.

**Cons:**
- More verbose than callbacks.

#### 3. Async/Await
Async/await is syntactic sugar built on top of promises, providing a more readable and synchronous-looking way to handle asynchronous operations.

**Example:**
```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve('Data fetched');
    }, 1000);
  });
}

async function fetchDataAsync() {
  try {
    const message = await fetchData();
    console.log(message); // Output after 1 second: Data fetched
  } catch (error) {
    console.error(error);
  }
}

fetchDataAsync();
```

**Pros:**
- More readable and maintainable code.
- Handles errors using try/catch blocks.

**Cons:**
- Requires understanding of promises.

### Summary
- **Callbacks**: Simple but can lead to callback hell.
- **Promises**: More structured and easier to chain, but verbose.
- **Async/Await**: Most readable and maintainable, built on promises.
