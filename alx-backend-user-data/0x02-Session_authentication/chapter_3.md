# How to Send Cookies

`Sending cookies` involves creating cookies on the server-side and sending them to the client (browser) as part of the `HTTP response`. The client then stores these cookies and sends them back with subsequent requests to the server.

### Analogy

Imagine you are a restaurant owner. When a customer visits, you give them a loyalty card (cookie) with their name on it. When they return, they show you the card, and you can greet them by name and offer personalized service.

## Step-by-Step Example Using Flask

We'll use Flask to demonstrate how to send cookies from the server to the client.

__Step 1: Setup__

1. __Install Flask__ (if you haven't already):

        pip install Flask

2. __Create a new file__, `app.py`, for your Flask application.

__Step 2: Sending a Cookie__

__app.py:__

    from flask import Flask, make_response, request

    app = Flask(__name__)

    @app.route('/')
    def index():
        username = request.cookies.get('username')
        if username:
            return f'Welcome back, {username}!'
        else:
            return 'Hello, Guest!'

    @app.route('/setcookie')
    def set_cookie():
        resp = make_response('Cookie has been set!')
        resp.set_cookie('username', 'Brendon', max_age=60*60*24*30)  # Cookie valid for 30 days
        return resp

    @app.route('/getcookie')
    def get_cookie():
        username = request.cookies.get('username')
        if username:
            return f'Found cookie! Username: {username}'
        else:
            return 'No cookie found!'

    @app.route('/deletecookie')
    def delete_cookie():
        resp = make_response('Cookie has been deleted!')
        resp.delete_cookie('username')
        return resp

    if __name__ == '__main__':
        app.run(debug=True)

## Explanation

1. __Flask Setup:__

      - Initializes the Flask application with Flask(__name__).
        
2. __Index Route (/):__

      - Checks if the username cookie exists and returns a personalized message if it does.
      - If the cookie doesn't exist, it returns a generic greeting.

3. __Set Cookie Route (/setcookie)__:

      - Creates a response with make_response and sets a username cookie with the value Brendon.
      - The max_age=60*60*24*30 parameter ensures the cookie is valid for 30 days.
      - The response with the cookie is sent back to the client.
        
4. Get Cookie Route (/getcookie):

      - Retrieves the username cookie value from the client's subsequent requests and returns it if it exists.

5. __Delete Cookie Route__ (`/deletecookie`):

   - Deletes the username cookie using resp.delete_cookie('username').
   - The response indicates that the cookie has been deleted.
  
## Summary

- __Sending Cookies__: Cookies are created on the server and sent to the client as part of the HTTP response headers.

- __Storing Cookies__: The client (browser) stores the cookies and sends them back with subsequent requests to the server.

- __Managing Cookies in Flask__:

   - Use `make_response` to create a response object.

   - Use `set_cookie` to attach cookies to the response.

   - Use `request.cookies` to read cookies from the client's request.

   - Use `delete_cookie` to remove cookies from the client's browser.
 
## Testing the Example

1. __Run the Flask Application__:

        python app.py

2. __Set a Cookie__:

   - Visit `http://localhost:5000/setcookie` in your browser to set the `username` cookie.
  
3. __Get the Cookie__:

   - Visit `http://localhost:5000/getcookie` to retrieve and display the `username` cookie.
  
4. __Delete the Cookie__:

   - Visit `http://localhost:5000/deletecookie` to delete the `username` cookie.
  
By following these steps, you can understand how ```cookies``` are `sent`, stored, and managed in ```web applications```.
