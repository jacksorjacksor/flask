# Standard file structure

## Rough explanations
venv: virtual environment
app.py or wsgi.py: redirects into your_actual_app folder
__init__.py: this file turns your_actual_app into a Python package and defines core app and database attributes
routes.py: defines the URL routing and method handling
models.py: defines the database schema (structure)
forms.py: defines all forms to be used on the site

## Typical structure
```
.
│   [ Not specific to Flask ]
├── .git
├── .gitignore
├── venv
│   [ Specific to Flask ]
├── app.py (or wsgi.py)
├── your_actual_app
│   ├── __init__.py
│   ├── routes.py
│   ├── models.py
│   ├── forms.py
│   ├── templates
│   │   └── [ all your .html files ]
│   ├── static
│   │   └── [ all your .css and .js files ]
```

Note that that the "static" directory has to be defined in the app:

__init__.py
```python
app = Flask(__name__, static_folder="static")
```

The "templates" directory is the named "templates" by default, but can be specified with the template_folder argument in the app:

__init__.py
```python
app = Flask(__name__, template_folder="a_different_folder_name")
```





