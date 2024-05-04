# 0x09_API (Application Programming Interface)

## Python

## Scripting

## Back-end

## API

## What Bash scripting should not be used for

- Bash scripting is powerful for automating tasks and managing system configurations in Unix-like environments. However, there are some scenarios where it's not the best choice:

1. Performance-Critical Applications: Bash scripting might not be suitable for applications that require high performance or complex computations. Other languages like C/C++ or Python are better options in such cases.

2. Large-Scale Applications: While Bash scripts can handle moderate-sized projects, they can become hard to maintain and scale in larger projects. Using more structured languages like Python or Ruby might be more appropriate for large-scale applications.

3. Cross-Platform Development: Bash scripting is primarily designed for Unix-like systems and may not work seamlessly across different operating systems. For cross-platform compatibility, languages like Python or Java are preferred.

## Real-world example (Bash scripting not suitable for performance-critical applications):

Developing a high-frequency trading system where microseconds matter for executing trades. In such scenarios, low-level languages like C/C++ are preferred for their ability to optimize performance.

## What is an API

- An API (Application Programming Interface) is a set of rules and protocols that allows different software applications to communicate with each other. It defines the methods and data formats that applications can use to request and exchange information.
- Its A Mechanism To Communicate And Exchange Data Between Two Services Or Applications
- API Stands For Application Programming Interface

## Real-world example (API):

1. The Google Maps API allows developers to integrate maps, geolocation services, and route planning into their applications. Developers can use the API to request map tiles, geocode addresses, and calculate directions.

## Lets Take An Example Of A Restaurant(API):

- A customer is A Client Application And A Chef is An Application Running On The Server.
- A waiter Acts As An API Who Takes An Order From The Customer And Communicates It To The Chef. Once The Food Is Ready. The Waiter Collects And Delivers It To The Customer.

## In The Technical Terms:

- A Client Applicaion Makes An HTTP Request Call To Another Application To Retrieve Some Data Via An API Call. The Application Running On The Server Processes The Request. Sometimes Fetches The Data From The Database And Sends The Response In The Format (JSON) That Client Application Wants.

## What is a REST API

- A REST API (Representational State Transfer API) is an architectural style for designing networked applications. It relies on a stateless, client-server communication protocol, typically HTTP, and uses standard HTTP methods like GET, POST, PUT, DELETE for performing CRUD (Create, Read, Update, Delete) operations on resources.

## Real-world example (REST API):

- The Twitter API provides access to Twitter's data and functionality, allowing developers to create applications that interact with Twitter's platform. It follows REST principles, where developers can perform actions like retrieving tweets, posting tweets, and searching for users.
i
## What are microservices

- Microservices are an architectural style where a complex application is composed of small, independent services that communicate with each other over a network. Each service is responsible for a specific business function and can be developed, deployed, and scaled independently.

## Real-world example (Microservices):

- Netflix uses a microservices architecture to power its streaming platform. Each microservice handles a specific aspect of the platform, such as user authentication, recommendation algorithms, content delivery, and billing. This allows Netflix to scale different components independently and deploy updates more frequently.

## What is the CSV format

CSV (Comma-Separated Values) is a simple file format used to store tabular data, such as a spreadsheet or a database. Each line in a CSV file represents a row of data, and the values within each row are separated by commas or other delimiters.

## Real-world example (CSV format):

 Exporting data from a spreadsheet software like Microsoft Excel or Google Sheets into a CSV file format. For instance, a sales team might export sales data from a spreadsheet to share with other departments or import into another system for analysis.

## What is the JSON format

- JSON (JavaScript Object Notation) is a lightweight data interchange format that is easy for humans to read and write and easy for machines to parse and generate. It is commonly used for transmitting data between a server and a web application as an alternative to XML.

## Real-world example (JSON format):

When interacting with a weather API, the response might be returned in JSON format, containing information such as temperature, humidity, wind speed, and forecast. Developers can parse this JSON data to display weather information in their applications.

## Pythonic naming conventions for packages, modules, classes, variables, functions, and constants typically follow these styles:

- Package/Module Names: lowercase_with_underscores
- Class Names: CapWords or CamelCase
- Variable Names: lowercase_with_underscores
- Function Names: lowercase_with_underscores
- Constant Names: UPPERCASE_WITH_UNDERSCORES

- CapWords or CamelCase in Python is significant as it helps improve readability and consistency within the codebase. By adhering to a consistent naming convention, it becomes easier for developers to understand and maintain the code.

## Real-world example (Pythonic naming conventions):

- Package/Module Names: numpy, pandas
- Class Names: HTTPRequest, CustomerService
- Variable Names: user_age, total_sales
- Function Names: calculate_discount, fetch_data
- Constant Names: MAX_RETRY_ATTEMPTS, PI_VALUE

## What are Different Types of APIs?

- There are many different types of APIs for operating systems, applications or websites. Windows, for example, has many API sets that are used by system hardware and applications — when you copy and paste text from one application to another, it is the API that allows that to work.

- Most operating environments, such as MS-Windows, provide APIs, allowing programmers to write applications consistent with the operating environment. Today, APIs are also specified by websites. For example, Amazon or eBay APIs allow developers to use the existing retail infrastructure to create specialized web stores. Third-party software developers also use Web APIs to create software solutions for end-users.

## What are Examples of Popular APIs?

- ProgrammableWeb, a site that tracks more than 15,500 APIs, lists Google Maps, Twitter, YouTube, Flickr and Amazon Product Advertising as some of the the most popular APIs. The following list contains several examples of popular APIs:

- 1. Google Maps API: The Google Maps API lets developers embed Google Maps on webpages using a JavaScript or Flash interface. The Google Maps API is designed to work on mobile devices and desktop browsers.

- 2. YouTube APIs: YouTube’s APIs let developers integrate YouTube videos and functionality into websites or applications. YouTube APIs include the YouTube Analytics API, YouTube Data API, YouTube Live Streaming API, YouTube Player APIs, and others.

- 3. Flickr API: The Flickr API is used by developers to access the Flick photo sharing community data. The Flickr API consists of a set of callable methods, and some API endpoints

- 4. Twitter APIs: Twitter offers two APIs. The REST API allows developers to access core Twitter data and the Search API provides methods for developers to interact with Twitter search and trends data.

- 5. Amazon Product Advertising API: Amazon’s Product Advertising API gives developers access to Amazon’s product selection and discovery functionality. Devs can then incorporate advertisements of  Amazon products to monetize a website.

## WWW and remote servers

- When I think about the Web, I imagine a large network of connected servers.

- Every page on the internet is stored somewhere on a remote server. A remote server is not so mystical after all — it’s just a part of a remotely located computer that is optimized to process requests.

- To put things in perspective, you can spin up a server on your laptop capable of serving an entire website to the Web (in fact, a local server is what engineers use to develop websites before releasing them to the public).

- When you type www.facebook.com into your browser, a request goes out to Facebook’s remote server. Once your browser receives the response, it interprets the code and displays the page.

- To the browser, also known as the client, Facebook’s server is an API. This means that every time you visit a page on the Web, you interact with some remote server’s API.

- An API isn’t the same as the remote server — rather it is the part of the server that receives requests and sends responses.

## What CORS means?

- 
CORS stands for Cross-Origin Resource Sharing. It is a security feature implemented by web browsers to control how web pages from one domain can access resources (like data or APIs) on another domain. This security mechanism is used to prevent unauthorized cross-origin requests that could pose potential security risks.

- Here's what CORS means and how it works with real-world examples:

## Explanation:

- When a web page makes a request to a different domain (i.e., different origin) via JavaScript (e.g., using fetch or XMLHttpRequest), the browser enforces CORS to determine whether the request is allowed. The server hosting the resource specifies in its response headers which origins are allowed to access the resource.

## Real-World Examples:

## 1. Cross-Origin API Requests:

- Suppose you have a frontend web application hosted on https://example.com that needs to fetch data from an API hosted on https://api.example.com. Without CORS, the browser would block these requests due to the different origins. By configuring CORS on the API server (https://api.example.com), it can specify that requests from https://example.com are allowed, enabling the frontend to fetch data securely.

## 2. Third-Party APIs:

- Consider a scenario where a website wants to embed content (like a map or social media feed) from a third-party service (e.g., Google Maps or Twitter) into its pages. The third-party service must allow cross-origin requests from the website's domain to access their resources. This is often achieved by configuring CORS settings on the third-party service's servers.

## 3. Single-Origin Policy (SOP) Bypass:

- CORS helps enforce the Single-Origin Policy (SOP) implemented by web browsers, which restricts scripts running in a web page from making requests to different origins. By configuring CORS policies on servers, specific cross-origin requests can be permitted while maintaining security.

- In summary, CORS is a security mechanism that allows controlled access to resources across different origins on the web. It enables secure data sharing and integration between web applications while preventing unauthorized access and potential security vulnerabilities.

