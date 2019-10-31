
# Week 5: UI Continued

cd into your templates folder to get started! 

1.  base.html
    

- Makes use of Bootstrap, a CSS framework that organizes elements of a webpage elegantly
    
-  Serves as a template page that all other pages in the web app will use so that they share a set format
    
-  Rename to base.html and drag “index.html” from the startbootstrap-grayscale directory and put it into templates folder and rename it to “base.html” by right clicking on file and then clicking on ‘Rename’
    
-  Open base.html and remove lines 70-160
    

-  Do this by dragging cursor from line 70 to line 160 and then hitting delete
    

- If you make a mistake, go under “Edit” and click undo and try again
    

- Change title in line 12 to “URL Shortener”:
    

> 	 	<title>URL Shortener</title>

    
-  Change line 44 to to create a little symbol in the corner with “URL Shortener”

    

>  `<i  class="fa fa-play-circle"></i> <span  class="light">URL</span>Shortener`

- Now refresh your web page and notice that it still says “hi.” so you have to add block content to it -> explain what wrapper file is, explain how it will show up
 
-   2 lines right after `</nav>` and before `</body>`, add:
   

    

> `{% block content %}{% endblock %}`

    
-  Jinja line that lets child templates (in this case index.html) extend from this one and override this line with “block content” that is defined in each child template
    
-  In  index.html add the following lines to the top to display the contents of the wrapper

>     {% extends "base.html" %}
>     
>     {% block content %}
>     
>     {% endblock %}

- Run it, preview will show no styling but some links etc, so the following updates to the path need to be made in base.html
    
- For the following sections, modify the <link href= > elements to contain “../static/” at the beginning, inside href:

-   Bootstrap Core CSS. Example:
  
> `<link  href="../static/css/bootstrap.min.css"  rel="stylesheet">`

- Custom CSS. Example:

>  `<link  href="../static/css/grayscale.css"  rel="stylesheet">`

  Font-Awesome CSS. Example:

> `<link  href="../static/font-awesome/css/font-awesome.min.css" 
> rel="stylesheet" type=”text/css”>`

 Run it.

Now the CSS is showing, but the background image is not there, we need the header class and container which holds the background image inside the block content of index.html

>     <header class=”intro”>
>     
>     <div class=”container”>
> 
>     // code
>      
>     </div>
>     
>     </header>

Run the file again to refresh the CSS cache.

- Now let’s clean up the view (base.html)

- Go to line 50
   
- After hidden class:

>     <li class="hidden">
>     
>     <a href="{{ url_for('index') }}"></a>
>     
>     </li>
    
3.  Adjust the list to create a “Home” button that redirects to index page (uses url_for to grab the domain you are currently on and adds /index)

>     <li>
>     
>     Add home below and leave out the url_for
>     
>     <a  class="page-scroll"  href="{{ url }}">Home</a>
>     
>     </li>

- Click on home and it shows contact route
    

  
  
  

Go back to the view and click on Home and it’ll show the /hello route, what happened there? It’s because index function in views.py is wrapped most closely by /hello route, now delete this route, add url_for in views.py

 Create a new file “index.html” in the templates folder.


