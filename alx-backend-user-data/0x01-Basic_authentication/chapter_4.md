 # Using Basic Authentication and Sending the Authorization Header

__Basic Authentication__ is a straightforward method used to authenticate users in `HTTP requests`. It involves sending a username and password in the HTTP request's Authorization header to gain access to a protected resource.

__How Basic Authentication Works__

1. __Request with Authentication Header__: The client (such as a web browser or an API client) sends a request to a server that requires authentication. The request includes an `Authorization` header with the credentials.

2. __Credentials Encoding__: The username and password are encoded in a specific format before being sent. In Basic Authentication, credentials are encoded using Base64 encoding.

3. __Server Response__: The server receives the request, decodes the credentials, and verifies them. If the credentials are valid, the server processes the request and responds with the requested resource. If invalid, the server returns a `401 Unauthorized response`.

## Steps for Basic Authentication

1. __Encode Credentials__: The username and password are combined into a string in the format `username:password`. This string is then encoded in Base64.

2. __Send the Authorization Header__: Include the encoded credentials in the `Authorization` header of the HTTP request using the format `Basic <encoded_credentials>`.

3. __Server Decodes and Verifies__: The server decodes the Base64 string back to the original username:password format, verifies the credentials, and responds accordingly.

Example

1. Encoding Credentials
   
Suppose the username is `user` and the password is `pass`. You would combine them into `user:pass`, then encode this string in Base64.

   - __Original String__: `user:pass`
   - __Base64 Encoded__: `dXNlcjpwYXNz`

2. __Authorization Header__
   
You include this encoded string in the `Authorization` header like this:

code

    Authorization: Basic dXNlcjpwYXNz

3. __Making a Request__
   
When making an HTTP request, you include the Authorization header as shown:

    import requests

    # Basic Authentication details
    username = 'user'
    password = 'pass'
    auth = (username, password)

    # Making a request
    response = requests.get('http://example.com/protected', auth=auth)

    # Print response content
    print(response.content)

In this Python example using the `requests` library:

- The `auth` parameter automatically handles the encoding of credentials.
  
The `requests.get` method sends the Authorization header with the Base64-encoded credentials to the server.

## Practical Use Case

__Scenario__: Accessing a protected API endpoint that requires authentication.

Request:

code

    GET /api/resource HTTP/1.1
    Host: api.example.com
    Authorization: Basic dXNlcjpwYXNz
    
__Server Response__:

- __If credentials are valid__: The server returns the requested resource.

- __If credentials are invalid__: The server responds with `401 Unauthorized`, indicating that authentication is required or the provided credentials are incorrect.

__Security Note__

- __Not Secure on Its Own__: Basic Authentication sends credentials encoded but not encrypted, so it is not secure on its own. It's recommended to use Basic Authentication over HTTPS to encrypt the entire communication channel.

- __Use Case__: Basic Authentication is typically used in situations where security is less critical or for internal applications where HTTPS is used.

_Basic Authentication_ is simple and easy to implement but should be used with care due to its limitations in security.

## Python Example

Here's how to manually create the `Authorization` header and send it with a request:

python code

    import base64
    import requests

    # Define your credentials
    username = 'user'
    password = 'pass'

    # Format the credentials in 'username:password' format
    credentials = f'{username}:{password}'

    # Encode the credentials in Base64
    encoded_credentials = base64.b64encode(credentials.encode('utf-8')).decode('utf-8')

    # Define the URL of the resource
    url = 'http://example.com/api/resource'

    # Create the headers with the Base64-encoded credentials
    headers = {
    'Authorization': f'Basic {encoded_credentials}'
    }

    # Send the GET request with the custom Authorization header
    response = requests.get(url, headers=headers)

    # Print the response status and content
    print(f"Status Code: {response.status_code}")
    print(f"Response Text: {response.text}")

Explanation:

1. __import base64 and import requests__: Import the necessary libraries.

2. __username = 'user' and password = 'pass'__: Define your credentials.

3. __credentials = f'{username}:{password}'__: Format the credentials.

4. __base64.b64encode(credentials.encode('utf-8'))__: Encode the credentials in Base64.

5. __encoded_credentials.decode('utf-8')__: Convert the Base64-encoded bytes to a string.

6. __headers = {'Authorization'__: f'Basic {encoded_credentials}'}: Create the Authorization header.

7. __requests.get(url, headers=headers)__: Send the GET request with the custom header.

8. __response.status_code and response.text__: Retrieve and print the response status and body.

**Output**:

_code_

    Status Code: 200
    Response Text: <Content from the resource>
