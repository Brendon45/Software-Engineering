# How to Parse Cookies

`Parsing cookies` involves reading the cookies sent by the client's browser and extracting the values for use in your ```web application```. Cookies are sent by the client as part of the `HTTP request headers`.

### Analogy

Imagine you are a librarian. When a regular visitor (user) enters the library, they hand you their library card (cookie). You read the card to see the visitor's name and other details, allowing you to provide personalized service.

## Parsing Cookies in a Web Application

Let's continue with our Flask example to demonstrate how to parse cookies.

## Step-by-Step Example Using Flask

__Step 1: Setup__

1. __Install Flask__ (if you haven't already):

        pip install Flask

2. Create a new file, `app.py`, for your Flask application.

__Step 2: Parsing Cookies__

__app.py:__

    from flask import Flask, request, make_response

    app = Flask(__name__)

    @app.route('/')
    def index():
        # Retrieve the username cookie
        username = request.cookies.get('username')
        if username:
            return f'Welcome back, {username}!'
        else:
            return 'Hello, Guest!'

    @app.route('/setcookie')
    def set_cookie():
        # Create a response and set a cookie
        resp = make_response('Cookie has been set!')
        resp.set_cookie('username', 'Brendon', max_age=60*60*24*30)  # Cookie valid for 30 days
        return resp

    @app.route('/getcookie')
    def get_cookie():
        # Parse and display the cookie
        username = request.cookies.get('username')
        if username:
            return f'Found cookie! Username: {username}'
        else:
            return 'No cookie found!'

    @app.route('/deletecookie')
    def delete_cookie():
        # Delete the cookie
        resp = make_response('Cookie has been deleted!')
        resp.delete_cookie('username')
        return resp

    if __name__ == '__main__':
        app.run(debug=True)

## Explanation

1. __Flask Setup__:

    - Initializes the Flask application with `Flask(__name__)`.

2. __Index Route (/)__:

    - Reads the `username` cookie using `request.cookies.get('username')`.
    - If the cookie exists, it returns a personalized message. If not, it returns a generic greeting.
  
3. __Set Cookie Route (`/setcookie`)__:

    - Creates a response using `make_response`.
    - Sets a `username` cookie with the value `Brendon` using `resp.set_cookie('username', 'Cobby', max_age=60*60*24*30)`.

4. __Get Cookie Route (`/getcookie`)__:

    - Reads and displays the `username` cookie using `request.cookies.get('username')`.
  
5. __Delete Cookie Route (`/deletecookie`)__:

    - Deletes the `username` cookie using `resp.delete_cookie('username')`.
  
## Summary

- __Parsing Cookies__: Cookies sent by the client's browser can be read and parsed using the `request.cookies` object in Flask.

- __Reading Cookies__: Use `request.cookies.get(cookie_name)` to read a specific cookie value.

- __Managing Cookies__: You can set, read, and delete cookies using simple methods in Flask.

## Testing the Example

1. __Run the Flask Application__:

        python app.py

2. __Set a Cookie__:

   - Visit `http://localhost:5000/setcookie` in your browser to set the `username` cookie.
  
3. __Get the Cookie__:

  - Visit `http://localhost:5000/getcookie` to retrieve and display the `username` cookie.

4. __Delete the Cookie__:

  - Visit `http://localhost:5000/deletecookie` to delete the `username` cookie.

By following these steps, you can understand how to ```parse cookies``` and use their values in your ``web application``.
