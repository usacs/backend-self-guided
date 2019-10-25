# Week 2: Building a "Hello, World!" app
 
Hi! This week we will be building a simple “Hello, World” Flask app. This will create the base for our project, as well as demonstrate some basic features of Flask.


# Some helpful terminal commands

## Mac/Linux

**ls** - List all files in this directory level.

**cd <directory name>** - Change directory. Takes you into the name of the folder you type after the command. If there are spaces in the directory name, use quotes.

**mkdir <directory name>** - Make a new directory. Type the name of the folder you want to create after the command.

**touch <filename>** - Create a new file. Don’t forget the file extension! (e.g. .py for a python file)


## Windows

**dir** - List all files in this directory level. 

**cd <directory name>** - Change directory. Takes you into the name of the folder you type after the command. If there are spaces in the directory name, use quotes.

**mkdir <directory name>** - Make a new directory. Type the name of the folder you want to create after the command.

**type nul > <filename>** - Create a new file. Don’t forget the file extension! (e.g. .py for a python file)


# Creating the "Hello, World!" application

We will be creating this! Based on this: https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world

> 	from flask import Flask  
>  app = Flask(__ name __)    
>  @app.route('/')  
> 
>  def  hello_world():  
>          return  'Hello World!'  
> 
> if  __ name __  ==  '__ main __':   
	app.run()

## Installing Python 

Follow this link: https://www.python.org/downloads/ 

Choose the appropriate download for your operating system.

## Create directory structure

Now that you have Python installed, it's time to make your project folder. 

Change directory into whatever directory level you want to make your project folder in, and then create a folder called "url-shortener". See the guide above for the appropriate commands.

## Installing a virtual environment

Now we need to create a virtual environment to keep your installations contained within your main project directory. 

Use command **python3 -m venv venv**. This will create a directory in your project directory called "venv". 
Activate it using one of the following:

> **Mac**: source venv/bin/activate
>
> **Windows**: venv\Scripts\activate

You can deactivate the virtual environment once you're done working with the command "deactivate".

## Installing Flask extensions

Now we need to download Flask and any extensions we'll need, such as Flask-SQLAlchemy. This will allow us to connect our app to a SQL database. Use the following commands to install these in your virtual environment: 

> **pip install flask**: Installs Flask microframework<br/>
> **sudo pip install Flask Flask-SQLAlchemy**: Installs Flask and SQLAlchemy modules to global environment for a functional application and database

## Let's code!

Setup complete! Now it's time to create our app. 

### Create the file

First, create the main application file "app.py" within your main project directory. 

Then open it with your favorite built-in or text editor. I personally use vim.

### Set up as a Flask app 

Next we want to set it up as a Flask app. We need to import the Flask library and initalize the app with a Flask object:

> import flask from Flask<br/>
> app = Flask(__ name __)

Ignore the spaces around "name". (I had to include those because this is a markdown file and didn't want the underscores to be interpreted as formatting.)

### Create your first route

Now we are going to create a route. This will allow us to serve web pages. For now, our page will just display a string. In the future, it will display HMTL. 

Each route is a Python function, with an added decorator to tell Flask to treat it as a route. A decorator is a callable that takes a function as an argument and returns a replacement function. We will be using this one today:

> @app.route('/')

This creates a route for the app's default web address.

Underneath that, add:

>  def  hello_world():  
>          return  'Hello World!'  

This will ensure that the route will return the string "Hello World!" when called.

### Running the app

Add this so you can run your file as a normal python file (command: python3 app.py) and still serve it to the web:

> if  __ name __  ==  '__ main __':   
	app.run()
  
Alternatively, you can save, exit, and run the following commands: 

> **Mac**: export FLASK_APP=app.py<br/>
> **Windows**: set FLASK_APP=app.py

A link to your localhost should come up on your command line. If you copy and paste this into your browser, you should see "Hello, World!" in a new page on your browser.

Congrats! You've just created your first Flask app. Stay tuned to continue building on the project next week!
