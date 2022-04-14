---
layout: post
title: Flask Python Examples
author: john_doe
date: 2022-04-13 11:52:21
---
This is a collection of examples that highlight some awesome features of Flask, a Python web framework. If you're not familiar with Flask, it's a microframework that lets you quickly create an Python based Web application. 

Flask is a lightweight Python-based web framework. It is built on Werkzeug and Jinja2, two libraries that handle much of the heavy-lifting that other microframeworks require you to implement yourself.

One of the things we love about Flask is its ability to extend with modules, you can easily add different databases (MongoDB, MySQL, Postgres, SQLite). For example, you can use Flask-SQLAlchemy to create a SQL Alchemy ORM.

Flask lets you quickly create Python based web applications. So a great feature of Flask is its extensibility. There are many modules available that provide additional functionality, such as Flask-Login for user session management and Flask-Uploads for handling file uploads.

## Installation

Just install Flask via pip3: 

```
$ sudo pip3 install Flask
$ sudo pip3 install Flask
```

Go to python interactive mode to see the introduction and version of Flask.

```python
$ python3
>>> import flask
>>> print(flask.__doc__)
```
<br />

## Hello World

We write a web application that displays "Hello World!" using Flask, and see how to configure and debug Flask.

Create the Flask project HelloWorld with the following command:

```bash
mkdir HelloWorld
mkdir HelloWorld/static
mkdir HelloWorld/templates
touch HelloWorld/server.py
```
<br />

The static and templates directories are the default configuration, where static is used to store static resources, such as images, js, css files, etc. Templates stores template files.

Our website logic is basically in the *server.py* file, but of course, it is possible to give this file other names.

Add the following to server.py.

```python
from flask import Flask

app = Flask(__name__)
@app.route('/')
def hello_world():
    return 'Hello World!'

if __name__ == '__main__':
    app.run()
```

Run server.py.

```bash
$ python3 server.py 
* Running on http://127.0.0.1:5000/
```
<br />
Open a browser and visit http://127.0.0.1:5000/. Hello World! will appear on the browser page.
<br /><br />
The following message will be displayed in the terminal.

```
127.0.0.1 - - [16/May/2014 10:29:08] "GET / HTTP/1.1" 200 -
```

The variable app is a Flask instance, by the following.

```python
@app.route('/')
def hello_world():
    return 'Hello World!'
```

When the client accesses /, it will respond to the content returned by the hello_world() function. 

## Flask configuration

Remember you initialized your web app like this:

```python
app = Flask(__name__)
```
In the above code, the value of the python built-in variable __name__ is the string __main__ . The Flask class takes this parameter as the name of the program. This is of course customizable, e.g. app = Flask("my-app").

By default, Flask uses the static directory for static resources and the templates directory for templates, which can be changed by setting the following parameter

```python
app = Flask("my-app", static_folder="path1", template_folder="path2")
```


## Template

In large applications, putting business logic and presentation content together can increase code complexity and maintenance costs. You can split presentation into views. A web request returns a template (view).

A template is a file containing the response text, with a placeholder (variable) representing the dynamic part, telling the template engine that its specific value needs to be obtained from the data used.

Replacing variables with real values and returning the final string is a process called "rendering" Flask uses Jinja2, a template engine, to render templates.

Jinja2: is the next widely used template engine for Python, a template language implemented by Python, whose design ideas are derived from Django's template engine and extended with its syntax and a range of powerful features, its a template language built into Flask.

Template language: is a simple text format designed to automatically generate documents. In a template language, some variables are generally passed to the template, replacing pre-defined placeholder variable names in specific locations of the template.

```python
from flask import Flask,render_template

app = Flask(__name__, template_folder='C:/templates')

# Return a template
@app.route('/')
def hello_world():
    return render_template('index.html')

# Return other template for this url
@app.route('/list/')
def my_list():
    return render_template('posts/list.html')
```
<br />
When rendering a template using render_template, you can pass keyword arguments. You can use it directly in the template later.

If you have too many parameters, then you can put all of them into a dictionary and then use two asterisks when passing this dictionary parameter to break the dictionary into key parameters.

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def hello_world():
    context = {
        'username':'Sandra',
        'age': 35,
        'country': 'US',
        'childrens': {
            'name':'Tamara',
            'height': 175
        }
    }
    return render_template('index.html', **context)


@app.route('/name2/')
def say_name2():
    context = {
        'username':'Brendy',
        'age': 33,
        'country': 'US',
        'childrens': {
            'name':'Trevor',
            'height': 190
        }
    }
    return render_template('index.html', context=context)
   
if __name__ == '__main__':
    app.run(debug=True)
```
<br />
Then use a jinja2 template to render the data. Jinja2 is basically a webpage in html with Python variables displayed.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Person</title>
</head>
<body>
    <p>{{ username }}</p>
    <p>{{ age }}</p>
    <p>{{ country }}</p>
    <p>{{ childrens.name }}</p>
    <p>{{ childrens['name'] }}</p>
</body>
</html>
```