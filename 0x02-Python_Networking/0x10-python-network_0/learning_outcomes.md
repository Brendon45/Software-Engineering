## Welcome to 0x10. Python - Network #0 and grab some insights about networking

## Bash

## Python

## Scripting

## Back-end

## API

## 1. URL (Uniform Resource Locator):

- A URL is a reference or address that specifies the location of a resource on the internet. It consists of several components, including the scheme, domain name, path, query string, and fragment identifier.

- Real-life Example:
	- When you enter "https://www.google.com" into your browser's address bar, you are specifying the URL for Google's homepage.

## 2. HTTP (Hypertext Transfer Protocol):

- HTTP is the foundation of data communication for the World Wide Web. It is an application protocol that allows clients to request resources from servers and servers to respond with requested information.

- Real-life Example:
	- When you click on a link on a webpage to view another page, your browser sends an HTTP request to the server hosting that page.

## 3. Reading a URL:

- To read a URL, you can break it down into its components: scheme, domain name, path, query string, and fragment identifier. For example, in the URL "https://www.example.com/path/to/resource?query=value#section", the scheme is "https", the domain name is "www.example.com", the path is "/path/to/resource", the query string is "?query=value", and the fragment identifier is "#section".

- Real-life Example:
	- In the URL "https://www.amazon.com/books", "https" is the scheme, "www.amazon.com" is the domain name, and "/books" is the path.

## 4. Scheme for an HTTP URL:

- The scheme for an HTTP URL specifies the protocol used to access the resource. In "http://www.example.com", the scheme is "http".

- Real-life Example:
	- In "http://www.youtube.com", the "http" scheme indicates that the client is using HTTP to communicate with the server hosting YouTube.

## 5. Domain Name:

- A domain name is the human-readable name associated with an IP address on the internet. It identifies a specific location or organization online. For example, in "http://www.example.com", "example.com" is the domain name.

- Real-life Example:
	- The domain name "facebook.com" is used to access Facebook's website and services.

## 6. Subdomain:

- A domain name is the human-readable name associated with an IP address on the internet. It identifies a specific location or organization online. For example, in "http://www.example.com", "example.com" is the domain name.

- Real-life Example:
	- In "https://mail.google.com", "mail" is a subdomain used to access Gmail, a service provided by Google.

## 7. Defining a Port Number in a URL:

- A port number in a URL specifies the communication endpoint for the server. It follows the domain name and is preceded by a colon. For example, in "http://www.example.com:8080", "8080" is the port number.

- Real-life Example:
	 - In "https://www.example.com:8080", the port number "8080" specifies the port to use when connecting to the server hosting Example's website

## 8. Query String:

- A query string is a part of a URL that contains data to be passed to the server as key-value pairs. It follows the path and is preceded by a question mark. For example, in "http://www.example.com/search?q=query", "?q=query" is the query string.

- Real-life Example:
	-  In "https://www.google.com/search?q=python", the query string "?q=python" contains the search term "python" that Google will use to search for relevant results.

## 9. HTTP Request:

- An HTTP request is a message sent by a client to a server, requesting a specific action or resource. It consists of a request method, URL, headers, and optional body.

- Real-life Example:
	- When you submit a form on a website, your browser sends an HTTP POST request to the server with the form data.

## 10. HTTP Response:

- An HTTP response is a message sent by a server to a client in response to an HTTP request. It contains status information, headers, and an optional body with the requested resource or error message.

- Real-life Example:
	- When you visit a webpage, the server sends an HTTP response containing the HTML, CSS, and JavaScript code needed to render and display the page in your browser.

## 11. HTTP Headers:

- HTTP headers are additional pieces of information sent between the client and server along with the request or response. They provide metadata about the message, such as content type, length, and caching instructions.

- Real-life Example:
	- HTTP headers such as "Content-Type" and "Content-Length" are used to convey metadata about the data being transferred between the client and server.

## 12. HTTP Message Body:

- The HTTP message body contains the data or content associated with an HTTP request or response. It can include text, HTML, JSON, files, or any other type of data.

- Real-life Example:
	- The HTTP message body of a POST request might contain the data submitted in a form, such as the contents of an email or a comment.

## 13. HTTP Request Method:

- An HTTP request method indicates the desired action to be performed on a resource. Common methods include GET (retrieve), POST (submit), PUT (update), DELETE (remove), and PATCH (modify).

- Real-life Example:
	- When you click a link to view a webpage, your browser sends an HTTP GET request to the server hosting that page.

## 14. HTTP Response Status Code:

- An HTTP response status code indicates the outcome of an HTTP request. It provides information about whether the request was successful, redirected, or encountered an error. Common status codes include 200 (OK), 404 (Not Found), and 500 (Internal Server Error).

- Real-life Example:
	- A 404 status code indicates that the requested resource was not found on the server, commonly seen when a webpage or file is missing.

## 15. HTTP Cookie:

- An HTTP cookie is a small piece of data sent from a website and stored on the user's computer by the user's web browser. It is used to track user activity, maintain user sessions, and personalize the browsing experience.

- Real-life Example:
	- When you log into a website, the server may send a cookie to your browser to remember your login session and preferences for future visits.

## 16. Making a Request with cURL:

- cURL is a command-line tool for transferring data with URLs. You can make HTTP requests using cURL by specifying the desired method and URL. For example, curl -X GET http://www.example.com.

- Real-life Example:
	- You can use cURL to make HTTP requests from the command line, such as fetching data from a RESTful API or testing web services.

## 17. What Happens When You Type google.com in Your Browser (Application Level):

- When you type "google.com" in your browser and press Enter, the browser sends an HTTP request to the domain name system (DNS) server to resolve the domain name to an IP address. Once the IP address is obtained, the browser sends an HTTP request to the server at that IP address, requesting the default web page (usually the homepage). The server responds with an HTTP response containing the requested web page, which the browser then renders and displays to the user.

- Real-life Example:
	- Your browser sends an HTTP GET request to Google's servers, which respond with the HTML, CSS, and JavaScript code needed to render and display the Google homepage.
