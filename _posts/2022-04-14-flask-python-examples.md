---
layout: post
title: Flask Python Examples
author: john_doe
date: 2022-04-14 11:52:21
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

