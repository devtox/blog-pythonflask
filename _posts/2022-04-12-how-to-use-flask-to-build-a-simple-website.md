---
layout: post
title: How to Use Flask to Build a Simple Website
author: john_doe
date: 2022-04-13 00:00:01
---
Python Flask is a popular server-side web framework written in Python. It’s based on Werkzeug and Jinja 2. Flask is an extremely popular framework among developers and is used by thousands of websites and applications. In order to help get you familiar with how to use Flask, this tutorial will show you how to use Flask to build a simple website.

## Exploring Flask Features

Flask is one of many frameworks that are focused on helping you create web servers with Python. There are other frameworks available that you could use, but what makes Flask special? What makes Flask worth learning over one of its competitors? Let’s explore some of the features that make Flask stand out from the crowd.

In order to help keep this article shorter, I have decided to split it into two parts. This first part will provide an overview of the features that make Flask a good choice for developing web applications with Python.

## Installation of flask

On Linux systems: 

```
sudo pip3 install flask
sudo pip install flask
```

<br />

## Create Routes

A route is a mapping from a url like /guestbook to a Python function, such as guestbook(). This is not automatic. In flask, **@app.route()** is used to establish the route.

The route that should always exist is the index route.

```
@app.route('/')
```

This indicates the root path of the website, like localhost:5000/ in the browser.

```
@app.route('/')
@app.route('/index')
#type localhost:5000/ or localhost:5000/index in your browser to access
def index():
    return 'hello'
```

Finally, a simple flask program

```
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

## Routing with parameters

Basic routing with parameters is possible with Flask. In the example below the route /show1/ can end with any name parameter. 

```
@app.route('/show1/<name>')
#type localhost:5000/show1/xxx in the browser to access
def show1(name):
    #In the function name means the parameter passed on the address bar
    return '<h1>Name is: %s</h1>' % name
```
