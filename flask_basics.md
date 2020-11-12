# Flask Basics

Flask is a great Python microframework that can make building web sites and applications much faster. It offers some handy and reliable shortcuts and tools that'll make your web development life a lot easier.

### Basic Concepts

-   We call our Flask script an app.
-   The app is where all the requests come to.
-   The app then sends these requests to the right functions or view
-   The app finds these functions through the route.

### Example App

        from flask import Flask

        app = Flask(__name__)

        @app.route('/')
        def index():
            return "Hello, World!"

        app.run(debug=True, port=8000, host='0.0.0.0') # debug is true to reload everytime the code changes

### Flask templates

-   You can make flask render html templates in your views by using the object `render_template`.
-   Flask templates have what's called template inheritance.
-   This means templates can inherit from each other and just overrides parts.
-   The overridable parts are called _blocks_
