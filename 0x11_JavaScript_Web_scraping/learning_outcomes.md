# 0x11 JavaScript - Web scraping

## Scripting

## API

## JavaScript

## Why JavaScript programming is amazing

1. Versatility: JavaScript can be used for both client-side and server-side development, making it highly versatile. It powers web applications, mobile apps, server-side applications, and even desktop applications.

2. Ease of Learning: JavaScript is relatively easy to learn, especially for beginners. It has a syntax similar to other programming languages like C and Java, making it easier to grasp for those with prior programming experience.

3. Rich Ecosystem: JavaScript has a vast ecosystem of libraries, frameworks, and tools that make development faster and more efficient. From front-end frameworks like React and Angular to server-side frameworks like Node.js, there's a tool for almost every use case.

4. Asynchronous Programming: JavaScript supports asynchronous programming, which allows tasks to run concurrently without blocking the main thread. This is crucial for building responsive and efficient web applications.

5. Community Support: JavaScript has a large and active community of developers who contribute to open-source projects, share knowledge, and provide support through forums, tutorials, and documentation.

## How to manipulate JSON data

- To manipulate JSON data in JavaScript, you can use built-in methods provided by the language. Here's a basic example of how to manipulate JSON data:

// Sample JSON data

const jsonData = '{"name": "John", "age": 30, "city": "New York"}';

// Parse JSON string to JavaScript object

const obj = JSON.parse(jsonData);

// Accessing properties

console.log(obj.name); // Output: John

console.log(obj.age); // Output: 30

// Modifying properties

obj.age = 35;

// Converting JavaScript object back to JSON string

const updatedJsonData = JSON.stringify(obj);

console.log(updatedJsonData); // Output: {"name":"John","age":35,"city":"New York"}

## Explanation:

- In this code snippet, we have a JSON string stored in the jsonData variable.
- We use JSON.parse() to convert this JSON string into a JavaScript object (obj).
- We then access and modify properties of this object (obj.name, obj.age).
- Finally, we convert the modified JavaScript object back into a JSON string using JSON.stringify().
- Print the updatedJsonData using console.log

## To use the fetch API for making HTTP requests in JavaScript:

fetch('https://api.example.com/data')

  .then(response => response.json())

  .then(data => console.log(data))

  .catch(error => console.error('Error:', error));

## Explanation:

- This code snippet demonstrates how to use the fetch API to make an HTTP GET request to a specified URL (https://api.example.com/data).
- The fetch function returns a Promise that resolves to the Response object representing the response to the request.
- We use .then() to parse the response body as JSON using the .json() method.
- Finally, we chain another .then() to log the parsed JSON data to the console and a .catch() to handle any errors that may occur during the request.

## How to use request and fetch API

- To use the request module (if you're using Node.js):

const request = require('request');

request('https://api.example.com/data', function (error, response, body) {

  if (error) {

    console.error('Error:', error);

  } else {

    console.log('Body:', body);

  }

});

## Explanation:

- This code snippet demonstrates how to use the request module in a Node.js environment to make an HTTP GET request to a specified URL (https://api.example.com/data).
- We require the request module at the beginning of the script.
- We then use the request function to initiate an HTTP request, passing in the URL and a callback function to handle the response.
- Inside the callback function, we check for any errors (error) and log the response body (body) to the console if no errors occur.

## How to read and write a file using fs module

- To read and write a file using the fs module in Node.js:

const fs = require('fs');

// Reading a file

fs.readFile('example.txt', 'utf8', (err, data) => {

  if (err) {

    console.error('Error reading file:', err);

    return;

  }

  console.log('File content:', data);

});


// Writing to a file

const content = 'This is a sample text.';

fs.writeFile('example.txt', content, err => {

  if (err) {

    console.error('Error writing file:', err);

    return;

  }

  console.log('File has been saved.');

});

## Explanation:

- This code snippet demonstrates how to read and write files using the built-in fs (File System) module in Node.js.
- We require the fs module at the beginning of the script.
- We use the fs.readFile() function to asynchronously read the contents of a file named example.txt in UTF-8 encoding. We provide a callback function to handle any errors (err) and the data read from the file (data), which we log to the console.
- We use the fs.writeFile() function to asynchronously write data to a file named example.txt. We provide the file path, content, and a callback function to handle any errors (err). If the write operation is successful, we log a message indicating that the file has been saved.
- Both file read and write operations are asynchronous and non-blocking, allowing other tasks to continue while the file operations are in progress.
