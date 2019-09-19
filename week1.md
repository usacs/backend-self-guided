# Week 1: Introduction

Hi! Welcome to the backend self guided project, URL shortener. Here is this week's agenda.

## Agenda
1. Introduction
	- Web development
	- Flask
2. Begin technical setup
	- Notes on Directory Structure
	- Building "Hello World"

# Introduction to web development + Flask

Follow along **here**: https://docs.google.com/presentation/d/1jMNciAKopos4JMXy65NTUkRiLfqHTrTgldwqLoeAi9A/edit?usp=sharing

# Notes on Directory Structure

1.  Goal: Separate Front-End (HTML/CSS) from Back-End
2.  Done via directory structure
3.  General directory outline: (Bold = folder)
	-   **url-shortener**
		-   config.py
			-   Sets up the database configuration
		-   run.py
			-   Script that starts flask app when right clicking file and selecting Run
		-   url
			-   **Templates**
				-   base.html
					-   base code for bootstrap/CSS
				-   error.html
					-   html file that loads for general errors
				-   index.html
					-   jinja2 and takes variables in from .py files to be manipulated
			-   **Static**
				-   Contains CSS and JavaScript files
			-   **__init__.py**
				-   Called in run.py    
				-   Initializes global objects, including:
					-   Flask app object    
					-   Database objects
			-   models.py
				-   sets up tables for database
					-   a database can store multiple objects (by storing multiple tables)
					-   tables stores single objects (but can store many of the same object)
						-   table rows: individual objects
						-   table columns: object fields
			-   views.py
				-   Handles routing to HTML files defined in Templates folder and what is done within each of those pages

# Building a "Hello, World!" app

**Some notes:
-   The format that we will use to indicate a terminal command is:
$ __________________
type all code that is after the “$” sign
-   some useful terminal commands:
-   $ ls
	-   Prints out all files and directories in the current directories
-   $ cd ..
	-   Changes directory to its parent
-   $ vim <filedirectory>/<filename>
	-   Opens up the specified file in a text editor called vim in the terminal.
	-   While in vim:
		-   To edit:  press “i”  so you are in insert mode
		-   To exit:  esc -> “:wq”
	-   ex: vim url-shortener/__init__.py
	-   Note that while we will not be using vim during this tutorial, it is a good thing to know
1.  Setting up:
	- $ sudo pip install Flask Flask-SQLAlchemy
		- Installs Flask and SQLAlchemy modules to global environment for a functional application and database
	- $ mkdir url-shortener
		- Creates a new directory in current directory. This is where we will write our webapp to
		- Make hello world. Create example project directory and within it create a hello.py file

> 	from flask import Flask  
>  app = Flask(__ name __)    
>  @app.route('/')  
> 
>  def  hello_world():  
	>  return  'Hello World!'  
> 
> if  __ name __  ==  '__ main __':   
	app.run()

Run this using python hello.py, but it didn’t work what happened? Let’s look at this line from the server Important: use os.getenv(PORT, 8080) as the port and os.getenv(IP, 0.0.0.0) as the host in your scripts!, so cloud9 server output is asking us to use these variables for IP and PORT so first we add

"Import os" right after "from flask import Flask"

Then we modify the run by giving it these variables and make it look like below:

app.run(host=os.getenv(‘IP’, ‘0.0.0.0’, port=int(os.getenv(‘PORT’, 8080)))

Now retry and it works! Great, so we have a hello world but it’s not much of a web app is it so now let’s build out the structure of the app and directories we’ll need. We’ll create a folder that holds our application package, we’ll call it url, then within it we’ll create two more folders called static and templates. Static will hold all of our static assets (like javascript and css) and templates will hold all of our HTML files which will be the views of our app. Within the URL folder we’ll create two more files, one called config.py where we will hold the configuration variables (like database access stuff) and run.py which will be a different form of this hello.py we just created which will simply run the application. The way we’ll frame this app, the database will be sqlite and it’ll be stored in the url-shortener directory. Within the url folder which is where we’re storing our application assets, we will create 3 files, __init__.py, models.py and views.py which we will look at shortly, So let’s get started

-  $ cd url-shortener
	 - Changes directory to url-shortener so we are now looking inside the folder
   
-	$ mkdir url
    - Creates folder that holds the application package
- $ mkdir url/static
	-  Creates folder will hold static files (i.e. images, javascripts, and cascading style sheets (CSS))
-  $ mkdir url/templates
	- Creates folder to hold the website’s HTML files
    

2.  $ Right click url directory and create new file titled __ init __.py
    

> from flask import  Flask      
> app = Flask(__ name __)   
> from views import *

1.  __ init __.py is a simple init script. This code creates application object (of class Flask) and is initialized to the variable called app. We saw it in hello world where we did this all in one file.
    
2.  We will be inputting all variables from views. Putting import statement at the end avoids a circular reference because we will be importing url in views.py

3.  Right click url directory and create new file titled views.py
    

> from url import app      
> @app.route('/')  
>  @app.route('/hello')   
> def index():  
   ----return  "Hello, World!"

-  views is the handler that responds to requests from web browsers or other clients. In Flask, handlers are written as Python functions. Each view function is mapped to one or more request URLs.
  - This code creates two routes ‘www.test.com/’ and ‘www.text.com/index’ and each route will do different things depending on what functions are called, currently the function index() returns “Hello, World!”
    

4.  Right click url-shortener directory and create new file titled run.py
  

> from url import app #, db we will add the , db later   
> import os 
> if __ name __ == '__ main __':
> 
> #db.create_all() this line can be called later app.run(host=os.getenv('IP', '0.0.0.0'), port=int(os.getenv(‘PORT’,
> 8080)))

-  This starts up the development web server with our application
-  This script imports url variable from the url package and invokes its run method to start the server. The app variable holds the Flask instance that we created
-  Test out the root route, also go to the /hello route
    
**Please note**:

Tabbing/indenting is extremely important in Python. As there are no opening and closing brackets (i.e. { } ), indenting is how Python knows when an if-statement, function, etc. ends.



