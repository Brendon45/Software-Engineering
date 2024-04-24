# 0x10_ AirBnB clone - Web framework

## Python

## Back-end

## Webserver

## Flask

![GIVERY](https://miro.medium.com/v2/resize:fit:720/format:webp/1*L_QoAG863l8QvqxpNyBiqw.gif)

## What is a Web Framework

- A web framework is a software framework that is designed to support the development of web applications including web services, web resources, and web APIs. It provides a structured way to build and deploy web applications by offering tools, libraries, and APIs for handling common tasks such as routing, request handling, session management, and database interaction.

## Types of Web frameworks

- As web standards began to advance, the app logic shifted towards the client- ensuring smarter communication between the user and the web application. With logic on client-side, they (client) can react swiftly to user input. This makes web apps more responsive, easily navigate-able on any device. Thus, we have two functions of frameworks — a) the one to work on the server side, that helps to set up app logic on the server (backend) or b) to work on the client-side (front end).

![WEBSERVER](https://miro.medium.com/v2/resize:fit:720/format:webp/0*kHl1GyW0h7VkE1iy.png)

- The front-end frameworks mostly manage the external part of the website, i.e. what the user sees when they open the application. The back-end manages the internal part. Let’s take a deeper look

## 1. Server-side Frameworks

- The rules and architecture of the server-side frameworks permit you to create simple pages, landings and forms of different kinds. To create a web application with a well-developed interface you need a wider range of functionality. Server-side frameworks handle HTTP requests, database control and management, URL mapping, etc. These frameworks can improve security and form the output data- simplifying the development process. Some of the top server-side frameworks are –

- .NET (C#)

- Django (Python)

- Ruby on Rails (Ruby)

- Express (JavaScript/Node.JS)

- Symfony (PHP)

## 2. Client-side Frameworks

- Client-side frameworks don’t take care of the business logic like the server-side ones. They function inside the browser. Therefore, you can enhance and implement new user interfaces. A number of animated features can be created with frontend and single page applications. Every client-side framework varies in functionality and use. Here are some client-side frameworks for comparison’s sake; all of whom use JavaScript as their programming language-

- Angular

- Ember.JS

- Vue.JS

- React.JS

## What is a Flask?

-  is a lightweight web framework for Python that allows you to build web applications quickly and with minimal boilerplate code.Here's how you can build a simple web framework using Flask:

## 1. Install Flask:
You can install Flask using pip:

- pip install Flask

## 2. Define Routes:

In Flask, routes are URL patterns mapped to Python functions. You can define routes using the @app.route decorator. For example:

from flask import Flask

app = Flask(__name__)

@app.route('/')

def index():

    return 'Hello, World!'

if __name__ == '__main__':

    app.run(debug=True)

## 3. Handle Variables in Routes:
You can include variables in routes by using <variable_name> syntax in the route URL. For example:

@app.route('/user/<username>')

def show_user_profile(username):

    return f'User: {username}'

## 4. Templates:
- Templates in Flask are HTML files with placeholders for dynamic content. You can use the Jinja2 templating engine to create templates. For example:

<!-- template.html -->

<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>{{ title }}</title>

</head>

<body>

    <h1>Hello, {{ name }}!</h1>

</body>

</html>

## 5. Render Template:

- You can render a template in Flask using the render_template function. For example:

from flask import render_template

@app.route('/hello/<name>')

def hello(name=None):

    return render_template('template.html', name=name, title='Hello Page')

## 6. Dynamic Templates:

- Jinja2 templates support loops, conditions, and other control structures. For example:

<!-- dynamic_template.html -->

<ul>

{% for item in items %}

    <li>{{ item }}</li>

{% endfor %}

</ul>

## 7. Display Data from MySQL Database:

- You can use a database library like SQLAlchemy to interact with a MySQL database in Flask. Retrieve data from the database and pass it to the template for rendering. For example:

from flask_sqlalchemy import SQLAlchemy

app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql://username:password@localhost/db_name'

db = SQLAlchemy(app)

@app.route('/users')

def users():

    users = User.query.all()

    return render_template('users.html', users=users)

## Route:

- In web development, a route is a mapping between a URL pattern and a Python function that handles requests to that URL.

- When a user visits a specific URL in the browser, the associated route function is executed, and the response generated by that function is returned to the user's browser.

- Routes are defined using the @app.route decorator in Flask. The decorator takes the URL pattern as an argument.

- For example, @app.route('/hello') defines a route for the URL /hello.

## Template:

- A template is an HTML file with placeholders for dynamic content that can be filled in dynamically based on the context of the request.

- Templates allow you to separate the presentation layer (HTML) from the logic layer (Python code) in your web application, promoting better code organization and maintainability.

- Flask uses the Jinja2 templating engine, which provides features like template inheritance, conditional statements, loops, and variable interpolation.

- Templates are typically stored in a templates directory within your Flask project.

- For example, you might have a template named index.html that contains the structure of your homepage with placeholders for dynamic content.

## Dynamic Routing:

- Dynamic routing allows you to define routes with variable parts in the URL pattern.

- These variables capture values from the URL and pass them as arguments to the route function.

- Dynamic routing enables building dynamic web applications where the content served depends on the values passed in the URL.

- For example, a route /user/<username> captures the username from the URL and passes it to the route function for further processing.

## Rendering Templates:

- Rendering templates involves combining HTML templates with data to generate dynamic HTML responses.

- Flask provides a render_template function for rendering templates. This function takes the name of the template file as an argument and optional data to be passed to the template.

- Inside the template file, you can use Jinja2 syntax to access and display the passed data.

- For example, render_template('index.html', title='Welcome') renders the index.html template with the title variable set to 'Welcome'.

## Database Integration:

- Flask allows integration with databases to store and retrieve data for web applications.

- SQLAlchemy is a popular ORM (Object-Relational Mapping) library for database management in Flask.

- With SQLAlchemy, you can define database models as Python classes and interact with the database using these models.

- Data retrieved from the database can be passed to templates for rendering dynamic content in HTML pages.

## A Minimal Application

- A minimal Flask application looks something like this:

from flask import Flask

app = Flask(__name__)

@app.route("/")

def hello_world():

    return "<p>Hello, World!</p>"

- So what did that code do?

1. First we imported the Flask class. An instance of this class will be our WSGI application.

2. Next we create an instance of this class. The first argument is the name of the application’s module or package. __name__ is a convenient shortcut for this that is appropriate for most cases. This is needed so that Flask knows where to look for resources such as templates and static files.

3. We then use the route() decorator to tell Flask what URL should trigger our function.

4. The function returns the message we want to display in the user’s browser. The default content type is HTML, so HTML in the string will be rendered by the browser.

- Save it as hello.py or something similar. Make sure to not call your application flask.py because this would conflict with Flask itself.

- To run the application, use the flask command or python -m flask. You need to tell the Flask where your application is with the --app option.

$ flask --app hello run

 * Serving Flask app 'hello'

 * Running on http://127.0.0.1:5000 (Press CTRL+C to quit)

## Jinja

- A Jinja template is simply a text file. Jinja can generate any text-based format (HTML, XML, CSV, LaTeX, etc.). A Jinja template doesn’t need to have a specific extension: .html, .xml, or any other extension is just fine.

- A template contains variables and/or expressions, which get replaced with values when a template is rendered; and tags, which control the logic of the template. The template syntax is heavily inspired by Django and Python.

- Below is a minimal template that illustrates a few basics using the default Jinja configuration. We will cover the details later in this document:

<!DOCTYPE html>

<html lang="en">

<head>

    <title>My Webpage</title>

</head>

<body>

    <ul id="navigation">

    {% for item in navigation %}

        <li><a href="{{ item.href }}">{{ item.caption }}</a></li>

    {% endfor %}

    </ul>

    <h1>My Webpage</h1>
    {{ a_variable }}


    {# a comment #}
</body>

</html>

- The following example shows the default configuration settings. An application developer can change the syntax configuration from {% foo %} to <% foo %>, or something similar.

- There are a few kinds of delimiters. The default Jinja delimiters are configured as follows:

{% ... %} for Statements

{{ ... }} for Expressions to print to the template output

{# ... #} for Comments not included in the template output

#  ... ## for Line Statements
