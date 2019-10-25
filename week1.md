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



