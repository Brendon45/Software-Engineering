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

## To use the fetch API for making HTTP requests in JavaScript:

fetch('https://api.example.com/data')

  .then(response => response.json())

  .then(data => console.log(data))

  .catch(error => console.error('Error:', error));

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





