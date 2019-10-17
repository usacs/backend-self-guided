# Week 4: User Interface

Hi! Welcome to week 4. This week we will be finishing the database setup and starting the user interface.

# Creating and running the database

In your app.py file, add "db" after app and after the "if __ name __" line, add db.create_all() to create the database if it doesn’t already exist.

### Running the script
1.  Run your app,py file (command: python3 app.py)
2.  At this point, try out /hello and /index routes as well, ensure they show differences, pretty much can respond with whatever you define in the function wrapped by the route.
3.  First, notice db.sqlite file got created.

### Testing out the database connection
Once the url fails add this to app.py after the "if __name__ == '__main__':" line:

app.debug = True

Next, we're going to make the route to create the URLs. Add the following code to app,py:

    from url.models import URLMap
    
    @app.route('/urls')
    def urls():
	    urls = URLMap.query.all()
	    if len(urls) < 1: 		# if an empty URL is provided, do this by default 
		    url = URLMap(long_url="http://google.com", short_url="google")    
		    db.session.add(url)  
		    db.session.commit()
		    return  "Added first entry to DB!"
	    else:
		    return  "First entry is " + urls[0].long_url + “ at /” +
    urls[0].short_url

We will test this next week, as we need to make sure SQLite is properly set up. There are also some commands to learn to play around with the database.

# UI View - Forms and Input

In this section, we'll be creating HTML files for our app to serve. This way we can create more nuanced web pages and options for our users.

See the helloworld route in app.py? Change the return value from "Hello World" to "render_template("index.html")". 

    return render_template("index.html")

This will render an HTML file called "index.html" instead of just the string "Hello World". Later we'll create this HTML file.

We also need to import the "render_template" method, so at the end of the line that begins "from flask import Flask", add ", render_template" to the end:

    from flask import Flask, ... , render_template

Now it's time to create our HTML file. cd into your templates folder and create a file called "index.html". 

Let's use a ready-made theme to make it look nice.

HTML/CSS files
1.  Obtaining CSS folder
	a. Download greyscale theme with command:
$ wget [https://github.com/BlackrockDigital/startbootstrap-grayscale/archive/v1.0.6.zip](https://github.com/BlackrockDigital/startbootstrap-grayscale/archive/v1.0.6.zip)
2. Extract the .zip file:
3.  $ unzip v1.0.6.zip press tab (dumbass)
4. Drag unzipped file (titled “startbootstrap-grayscale”) into the static folder: /workspace/url-shortener/url/static
5. Click and drag every file and folder from inside “startbootstrap-grayscale” to the outer folder, titled “static”. - highlight all and move to static. If you haven't created a static folder yet, create one in your url folder.
