1. What is async/await?
Answer:
Async/await is syntactic sugar built on top of promises that allows you to write asynchronous code that looks synchronous. An async function always returns a promise, and await can only be used inside an async function to pause execution until the promise settles.

2. How to handle errors with async/await?
Answer:

javascript
async function fetchData() {
  try {
    const response = await fetch('url');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
    throw error; // Re-throw if you want calling code to handle it
  }
}
3. Can you use await with non-promise values?
Answer:
Yes, if you await a non-promise value, it's automatically wrapped in a resolved promise.

4. How to run async operations in parallel?
Answer:

javascript
async function parallel() {
  const [result1, result2] = await Promise.all([asyncOp1(), asyncOp2()]);
  // Use results
}
5. What's the difference between async/await and promises?
Answer:

Async/await makes asynchronous code look synchronous and easier to read

Error handling is simpler with try/catch blocks

Debugging is easier as the call stack is more straightforward

Under the hood, async/await still uses promises

HTTP Requests Questions
1. What are the different HTTP methods?
Answer:

GET: Retrieve data

POST: Send data to create a resource

PUT: Update an existing resource

PATCH: Partially update a resource

DELETE: Remove a resource

HEAD: Similar to GET but without response body

OPTIONS: Returns supported HTTP methods

2. What is the difference between GET and POST?
Answer:

GET requests are cached, remain in browser history, can be bookmarked, and have length restrictions

POST requests are never cached, don't remain in browser history, can't be bookmarked, and have no restrictions on data length

GET sends data in URL, POST sends data in request body

3. What are HTTP status codes?
Answer:

1xx: Informational

2xx: Success (200 OK, 201 Created, 204 No Content)

3xx: Redirection (301 Moved Permanently, 304 Not Modified)

4xx: Client errors (400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found)

5xx: Server errors (500 Internal Server Error, 503 Service Unavailable)

4. How to make HTTP requests in JavaScript?
Answer:

javascript
// Using Fetch API
fetch('url')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));

// Using XMLHttpRequest
const xhr = new XMLHttpRequest();
xhr.open('GET', 'url');
xhr.onload = function() {
  if (xhr.status === 200) {
    console.log(xhr.response);
  }
};
xhr.send();
5. What is CORS?
Answer:
Cross-Origin Resource Sharing (CORS) is a mechanism that allows restricted resources on a web page to be requested from another domain outside the domain from which the first resource was served. It's a security feature implemented by browsers.

Axios Questions
1. What is Axios?
Answer:
Axios is a promise-based HTTP client for the browser and Node.js that provides an easy-to-use API for making HTTP requests.

2. How to make a GET request with Axios?
Answer:

javascript
axios.get('url')
  .then(response => console.log(response.data))
  .catch(error => console.error(error));
3. How to make a POST request with Axios?
Answer:

javascript
axios.post('url', { key: 'value' })
  .then(response => console.log(response.data))
  .catch(error => console.error(error));
4. How to set default headers in Axios?
Answer:

javascript
axios.defaults.headers.common['Authorization'] = 'Bearer token';
5. How to handle errors in Axios?
Answer:

javascript
axios.get('url')
  .then(response => console.log(response.data))
  .catch(error => {
    if (error.response) {
      // Server responded with status code outside 2xx
      console.log(error.response.data);
      console.log(error.response.status);
    } else if (error.request) {
      // Request made but no response received
      console.log(error.request);
    } else {
      // Something else happened
      console.log('Error', error.message);
    }
  });
To create a PDF from this content:

Copy all the text above

Paste it into a Word document or Google Docs

Format it as needed

Save/Export as PDF

Would you like me to provide more questions on any specific topic or explain any answer in more detail?

Provide all questions that is 100
Here's a comprehensive list of 100 frequently asked JavaScript interview questions covering Arrays, Strings, Promises, async/await, HTTP requests, and Axios:

Arrays (30 Questions)
How to remove duplicates from an array?

How to find the sum of all elements in an array?

How to merge two arrays?

How to find the largest element in an array?

How to find the smallest element in an array?

How to check if a variable is an array?

How to find the index of an element in an array?

How to remove an element from an array by index?

How to check if an array includes a value?

How to sort an array in ascending/descending order

Provide all questions that is 100 with answer of each
Here's a comprehensive list of 100 JavaScript interview questions with answers, covering Arrays, Strings, Promises, async/await, HTTP requests, and Axios.

Arrays (30 Questions)
1. How to remove duplicates from an array?
Answer:

javascript
// Using Set
const uniqueArray = [...new Set(array)];

// Using filter
const uniqueArray = array.filter((item, index) => array.indexOf(item) === index);
2. How to find the sum of all elements in an array?
Answer:

javascript
const sum = array.reduce((acc, curr) => acc + curr, 0);
3. How to merge two arrays?
Answer:

javascript
// Using spread operator
const merged = [...array1, ...array2];

// Using concat
const merged = array1.concat(array2);
4. How to find the largest element in an array?
Answer:

javascript
const largest = Math.max(...array);
5. How to find the smallest element in an array?
Answer:

javascript
const smallest = Math.min(...array);
6. How to check if a variable is an array?
Answer:

javascript
Array.isArray(variable);
7. How to find the index of an element in an array?
Answer:

javascript
const index = array.indexOf(element);
8. How to remove an element from an array by index?
Answer:

javascript
// Using splice
array.splice(index, 1);

// Using filter (immutable)
const newArray = array.filter((_, i) => i !== index);
9. How to check if an array includes a value?
Answer:

javascript
const exists = array.includes(value);
10. How to sort an array in ascending order?
Answer:

javascript
array.sort((a, b) => a - b);
11. How to sort an array in descending order?
Answer:

javascript
array.sort((a, b) => b - a);
12. How to reverse an array?
Answer:

javascript
array.reverse();
13. How to convert an array to a string?
Answer:

javascript
const str = array.join(', '); // Comma-separated
14. How to find the intersection of two arrays?
Answer:

javascript
const intersection = array1.filter(value => array2.includes(value));
15. How to find the difference between two arrays?
Answer:

javascript
const difference = array1.filter(value => !array2.includes(value));
16. How to flatten a nested array?
Answer:

javascript
const flatArray = array.flat(Infinity);
17. How to check if all elements in an array satisfy a condition?
Answer:

javascript
const allPass = array.every(item => item > 0);
18. How to check if any element in an array satisfies a condition?
Answer:

javascript
const anyPass = array.some(item => item > 0);
19. How to map an array to a new array with modified values?
Answer:

javascript
const newArray = array.map(item => item * 2);
20. How to filter an array based on a condition?
Answer:

javascript
const filteredArray = array.filter(item => item > 10);
21. How to find the first element in an array that matches a condition?
Answer:

javascript
const found = array.find(item => item > 10);
22. How to find the index of the first element that matches a condition?
Answer:

javascript
const foundIndex = array.findIndex(item => item > 10);
23. How to initialize an array with default values?
Answer:

javascript
const newArray = new Array(5).fill(0); // [0, 0, 0, 0, 0]
24. How to loop through an array?
Answer:

javascript
// forEach
array.forEach(item => console.log(item));

// for...of
for (const item of array) {
  console.log(item);
}
25. How to copy an array (shallow vs deep copy)?
Answer:

javascript
// Shallow copy
const copy = [...array];

// Deep copy (for nested objects)
const deepCopy = JSON.parse(JSON.stringify(array));
26. How to remove falsy values from an array?
Answer:

javascript
const truthyArray = array.filter(Boolean);
27. How to split an array into chunks?
Answer:

javascript
const chunk = (arr, size) => 
  Array.from({ length: Math.ceil(arr.length / size) }, (_, i) =>
    arr.slice(i * size, i * size + size)
  );
28. How to shuffle an array?
Answer:

javascript
const shuffled = [...array].sort(() => Math.random() - 0.5);
29. How to find the average of an array?
Answer:

javascript
const avg = array.reduce((a, b) => a + b, 0) / array.length;
30. How to check if two arrays are equal?
Answer:

javascript
const areEqual = (arr1, arr2) => 
  arr1.length === arr2.length && arr1.every((val, i) => val === arr2[i]);
Strings (20 Questions)
31. How to reverse a string?
Answer:

javascript
const reversed = str.split('').reverse().join('');
32. How to check if a string is a palindrome?
Answer:

javascript
function isPalindrome(str) {
  const cleaned = str.replace(/[^A-Za-z0-9]/g, '').toLowerCase();
  return cleaned === cleaned.split('').reverse().join('');
}
33. How to count vowels in a string?
Answer:

javascript
const count = str.match(/[aeiou]/gi)?.length || 0;
34. How to capitalize the first letter of each word?
Answer:

javascript
const capitalized = str.replace(/\b\w/g, char => char.toUpperCase());
35. How to check if two strings are anagrams?
Answer:

javascript
function areAnagrams(str1, str2) {
  const normalize = str => str.replace(/\W/g, '').toLowerCase().split('').sort().join('');
  return normalize(str1) === normalize(str2);
}
36. How to truncate a string after a certain length?
Answer:

javascript
const truncated = str.length > max ? str.substring(0, max) + '...' : str;
37. How to count occurrences of a substring?
Answer:

javascript
const count = str.split(substring).length - 1;
38. How to remove whitespace from a string?
Answer:

javascript
const trimmed = str.trim(); // Removes start/end whitespace
const noSpaces = str.replace(/\s+/g, ''); // Removes all whitespace
39. How to convert a string to title case?
Answer:

javascript
const titleCase = str.replace(/\w\S*/g, txt => txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase());
40. How to check if a string starts/ends with a substring?
Answer:

javascript
const startsWith = str.startsWith('Hello');
const endsWith = str.endsWith('World');
41. How to repeat a string N times?
Answer:

javascript
const repeated = 'abc'.repeat(3); // 'abcabcabc'
42. How to pad a string with characters?
Answer:

javascript
const padded = str.padStart(10, '-'); // "-----hello"
43. How to extract numbers from a string?
Answer:

javascript
const numbers = str.match(/\d+/g).map(Number);
44. How to replace all occurrences of a substring?
Answer:

javascript
const replaced = str.replace(/old/g, 'new');
45. How to split a string into an array?
Answer:

javascript
const arr = str.split(' ');
46. How to check if a string contains only digits?
Answer:

javascript
const isDigits = /^\d+$/.test(str);
47. How to convert a string to camelCase?
Answer:

javascript
const camelCase = str.replace(/(?:^\w|[A-Z]|\b\w|\s+)/g, (match, index) => 
  index === 0 ? match.toLowerCase() : match.toUpperCase()
).replace(/\s+/g, '');
48. How to encode/decode a URL?
Answer:

javascript
const encoded = encodeURIComponent(str);
const decoded = decodeURIComponent(encoded);
49. How to check if a string is empty?
Answer:

javascript
const isEmpty = str.trim().length === 0;
50. How to get the first/last character of a string?
Answer:

javascript
const firstChar = str.charAt(0);
const lastChar = str.charAt(str.length - 1);
Promises (15 Questions)
51. What is a Promise in JavaScript?
Answer:
A Promise is an object representing the eventual completion (or failure) of an asynchronous operation. It has three states:

Pending (initial state)

Fulfilled (operation succeeded)

Rejected (operation failed)

52. How to create a Promise?
Answer:

javascript
const promise = new Promise((resolve, reject) => {
  if (success) resolve(value);
  else reject(error);
});
53. What are .then(), .catch(), and .finally()?
Answer:

.then() → Handles resolved promises

.catch() → Handles rejected promises

.finally() → Runs regardless of resolution/rejection

54. How to chain Promises?
Answer:

javascript
fetchData()
  .then(data => process(data))
  .then(result => console.log(result))
  .catch(error => console.error(error));
55. What is Promise.all()?
Answer:
Waits for all promises to resolve or any to reject:

javascript
Promise.all([promise1, promise2])
  .then(results => console.log(results))
  .catch(error => console.error(error));
56. What is Promise.race()?
Answer:
Returns the first settled promise (either resolved or rejected):

javascript
Promise.race([promise1, promise2])
  .then(result => console.log(result))
  .catch(error => console.error(error));
57. What is Promise.allSettled()?
Answer:
Waits for all promises to settle (resolve or reject) and returns an array of results:

javascript
Promise.allSettled([promise1, promise2])
  .then(results => results.forEach(result => console.log(result.status)));
58. How to handle multiple errors in Promise chains?
Answer:

javascript
fetchData()
  .then(step1)
  .catch(handleError1)
  .then(step2)
  .catch(handleError2);
59. How to convert a callback-based function to a Promise?
Answer:

javascript
function readFilePromise(path) {
  return new Promise((resolve, reject) => {
    fs.readFile(path, (err, data) => {
      if (err) reject(err);
      else resolve(data);
    });
  });
}
60. What is a "Promise anti-pattern"?
Answer:
Unnecessary Promise wrapping (e.g., new Promise inside .then()):

javascript
// ❌ Bad
.then(data => new Promise(resolve => resolve(process(data))));

// ✅ Good
.then(data => process(data));
61. How to cancel a Promise?
Answer:
Promises cannot be canceled, but you can use AbortController with fetch:

javascript
const controller = new AbortController();
fetch(url, { signal: controller.signal });
controller.abort(); // Cancels the request
62. What is "Promise hell"?
Answer:
Nested .then() chains that become hard to read (similar to callback hell):

javascript
fetchData()
  .then(data => {
    process(data)
      .then(result => {
        // Nested mess
      });
  });
63. How to retry a failed Promise?
Answer:

javascript
function retry(fn, retries = 3) {
  return fn().catch(err => 
    retries > 0 ? retry(fn, retries - 1) : Promise.reject(err)
  );
}
64. What is Promise.resolve() and Promise.reject()?
Answer:

Promise.resolve(value) → Creates a resolved promise

Promise.reject(error) → Creates a rejected promise

65. How to handle unhandled Promise rejections?
Answer:

javascript
process.on('unhandledRejection', (reason, promise) => {
  console.error('Unhandled Rejection:', reason);
});
Async/Await (15 Questions)
66. What is async/await?
Answer:
A syntactic sugar over Promises that makes asynchronous code look synchronous:

javascript
async function fetchData() {
  const data = await fetch(url);
  return data.json();
}
67. How to handle errors with async/await?
Answer:
Use try/catch:

javascript
async function fetchData() {
  try {
    const data = await fetch(url);
    return data.json();
  } catch (error) {
    console.error(error);
  }
}
68. Can await be used outside an async function?
Answer:
❌ No, it throws SyntaxError.

69. How to run async operations in parallel?
Answer:
Use Promise.all with await:

javascript
const [data1, data2] = await Promise.all([fetch(url1), fetch(url2)]);
70. What happens if you forget await?
Answer:
The function returns a pending Promise instead of the resolved value.

71. How to use async/await with forEach?
Answer:
forEach doesn’t work with await. Use for...of instead:

javascript
for (const item of array) {
  await asyncOperation(item);
}
72. How to make a class method async?
Answer:

javascript
class API {
  async fetchData() {
    return await fetch(url);
  }
}
73. Can you await a non-Promise value?
Answer:
✅ Yes, it wraps the value in a resolved Promise.

74. How to return early from an async function?
Answer:

javascript
async function checkUser(user) {
  if (!user) return false; // Early return
  return await fetchUser(user);
}
75. What is the difference between async/await and .then()?
Answer:

async/await is syntactic sugar for Promises

Makes code more readable (looks synchronous)

Easier error handling with try/catch

76. How to limit concurrent async operations?
Answer:
Use libraries like p-limit or implement a queue:

javascript
const limit = async (tasks, max) => {
  const results = [];
  for (const task of tasks) {
    if (running >= max) await Promise.race(runningTasks);
    runningTasks.push(task());
  }
  return Promise.all(runningTasks);
};
77. How to use async/await with setTimeout?
Answer:
Wrap setTimeout in a Promise:

javascript
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

await delay(1000);
78. How to test async/await functions?
Answer:
Use testing frameworks like Jest:

javascript
test('fetchData returns data', async () => {
  const data = await fetchData();
  expect(data).toBeDefined();
});
79. Can you await multiple times in a function?
Answer:
✅ Yes, but it runs sequentially. For parallelism, use Promise.all.

80. How to handle async/await in loops?
Answer:

Sequential: for...of

Parallel: Promise.all(array.map(async item => await fn(item)))

HTTP Requests (10 Questions)
81. What are the main HTTP methods?
Answer:

GET → Retrieve data

POST → Create data

PUT → Update data

DELETE → Remove data

PATCH → Partial update

82. What is the difference between GET and POST?
Answer:

GET	POST
Data in URL	Data in body
Cached	Not cached
Limited length	No length limit
83. What are common HTTP status codes?
Answer:

200 OK

201 Created

400 Bad Request

401 Unauthorized

404 Not Found

500 Server Error

84. How to make an HTTP request in JavaScript?
Answer:
Using fetch:

javascript
fetch('https://api.example.com/data')
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));
85. What is CORS?
Answer:
Cross-Origin Resource Sharing → A security feature that restricts cross-origin HTTP requests.

86. How to send headers with fetch?
Answer:

javascript
fetch(url, {
  headers: {
    'Authorization': 'Bearer token',
    'Content-Type': 'application/json'
  }
});
87. How to send a POST request with JSON data?
Answer:

javascript
fetch(url, {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ key: 'value' })
});
88. What is the difference between fetch and XMLHttpRequest?
Answer:

fetch → Modern, Promise-based

XHR → Older, callback-based

89. How to handle HTTP errors with fetch?
Answer:
Check response.ok:

javascript
fetch(url)
  .then(res => {
    if (!res.ok) throw new Error('HTTP error');
    return res.json();
  });
90. How to cancel an HTTP request?
Answer:
Use AbortController:

javascript
const controller = new AbortController();
fetch(url, { signal: controller.signal });
controller.abort(); // Cancel request
Axios (10 Questions)
91. What is Axios?
Answer:
A Promise-based HTTP client for browsers and Node.js.

92. How to make a GET request with Axios?
Answer:

javascript
axios.get('/user?ID=123')
  .then(res => console.log(res.data))
  .catch(err => console.error(err));
93. How to make a POST request with Axios?
Answer:

javascript
axios.post('/user', { name: 'John' })
  .then(res => console.log(res.data));
94. How to set default headers in Axios?
Answer:

javascript
axios.defaults.headers.common['Authorization'] = 'Bearer token';
95. How to handle errors in Axios?
Answer:

javascript
axios.get(url)
  .catch(err => {
    if (err.response) {
      console.log(err.response.status); // 404, 500, etc.
    }
  });
96. How to send query parameters with Axios?
Answer:

javascript
axios.get('/user', { params: { ID: 123 } });
97. How to intercept requests/responses in Axios?
Answer:

javascript
axios.interceptors.request.use(config => {
  config.headers.Authorization = 'Bearer token';
  return config;
});
98. How to cancel an Axios request?
Answer:
Use CancelToken:

javascript
const source = axios.CancelToken.source();
axios.get(url, { cancelToken: source.token });
source.cancel('Request canceled');
99. How to use Axios in Node.js?
Answer:
Install via npm install axios:

javascript
const axios = require('axios');
axios.get('https://api.example.com/data')
  .then(res => console.log(res.data));
100. What are the advantages of Axios over fetch?
Answer:
✅ Built-in request/response interceptors
✅ Automatic JSON data transformation
✅ Error handling with status codes
✅ Request cancellation
✅ Works in Node.js and browsers