---
layout: post
title: How to Use Flask
author: john_doe
date: 2022-04-11 00:00:01
---
Python Flask is a popular server-side web framework written in Python. It’s based on Werkzeug and Jinja 2. Flask is an extremely popular framework among developers and is used by thousands of websites and applications. In order to help get you familiar with how to use Flask, this tutorial will show you how to use Flask to build a simple website.

## Exploring Flask Features

Flask is one of many frameworks that are focused on helping you create web servers with Python. There are other frameworks available that you could use, but what makes Flask special? What makes Flask worth learning over one of its competitors? Let’s explore some of the features that make Flask stand out from the crowd.

In order to help keep this article shorter, I have decided to split it into two parts. This first part will provide an overview of the features that make Flask a good choice for developing web applications with Python.

## Installation of flask

There are a few steps involved in installing Flask. First, you will need to install the Python 3 programming language on your computer. Then, you will need to install the Flask framework. Finally, you will need to create the software (a file called app.py) in order to run your Flask application.

Python 3 can be downloaded from the official Python website ([https://www.python.org/](https://www.python.org)). Once you have downloaded and installed Python 3, you will need to open up a new terminal window and type in the following command: *pip3 install flask*. This should begin the process of installing Flask on your computer.

It's recommended to install Flask inside a project environment (virtual environment), so that the version your program depends on doesn't conflict with your system.To do so, make sure virtualenv is installed, you can do so with pip:

```bash
pip install virtualenv
```

Then setup the virtual environment 

```bash
mkdir newproj
cd newproj
virtualenv venv
```

Then active the environment

```bash
# linux
venv/bin/activate
# windows
venv\scripts\activate
```

And finally, install Flask and whichever other modules you need in that virtual environment.

```
pip3 install flask
```

After Flask has finished installing, you will need to create a new file called app.py in order to write your code. You can do this using any text editor such as VSCode or vim.

<br />

## Create Routes

A route is a mapping from a url like /guestbook to a Python function, such as guestbook(). This is not automatic. In flask, **@app.route()** is used to establish the route.

The route that should always exist is the index route.

```python
@app.route('/')
```

This indicates the root path of the website, like localhost:5000/ in the browser.

```python
@app.route('/')
@app.route('/index')
#type localhost:5000/ or localhost:5000/index in your browser to access
def index():
    return 'hello'
```

<br />

Finally, a simple flask program

```python
from flask import Flask

app = Flask(__name__)
@app.route('/')
def index():
    return "<h1>This is my first flask app</h1>"

if __name__ == '__main__':
    #run the Flask app (start Flask's service), the default port number to open on this machine is 5000.
    #debug=True, is to change the current startup mode to debug mode (debug mode is recommended in development environment, not allowed in production environment)
    app.run(debug=True)
```

<br />

![python flask web app](/assets/img/uploads/python-flask.png)

<br />

## Routing with parameters

Basic routing with parameters is possible with Flask. In the example below the route /show1/ can end with any name parameter. 

```python
@app.route('/show1/<name>')
#type localhost:5000/show1/xxx in the browser to access
def show1(name):
    #In the function name means the parameter passed on the address bar
    return '<h1>Name is: %s</h1>' % name
```

<br />

## Json

While functions can return strings (a sequence of characters) they can also return a set of key-value pairs known as json. This is very for both humans and computers to understand. That way you can even dump Python objects.

First import the json stuff:

```python
import json
from flask import jsonify
```

Second, there are two functions to know: dumps() and loads().

```python
json.dumps(): # convert the dictionary into a json string.
json.loads(): # convert json strings to dictionaries
```

They both operate on variables (variables are stored in memory).

That way you can return Python data like a dictionary, as a json object:

```python
@app.route('/')
def index():
    data = {
    'name':'Ana',
    'age':'24'
    }
    return json.dumps(data) 
```

<br />

## Template

You can return templates (code rendered onto html) and json also. To work with json, import the jsonify module. To return modules, you must import render_template from flask.

```python
from flask import jsonify
from flask import render_template

from app import app


@app.route("/")
def index():
    return render_template("index.html")


@app.route("/hello", methods=['GET', ])
def hello():
    return jsonify(msg="hello world!")
```