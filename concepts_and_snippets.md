# Concepts and Snippets

Lines prefaced with "$" symbol are written in the Terminal, in Git Bash.

## Terminal

Show Terminal if hidden:
[ Ctrl + ' ]

Print working directory
```
$ pwd
```

Load Windows Explorer in current working directory
```
$ explorer .
```

Load VS code in current working directory
```
$ code .
```

Autocompleting file paths in the terminal
[ After you've typed a bit, press Tab and the terminal will try to autocomplete ]

## Virtual environments ("venv")

Creating a virtual environment:
```
$ py -m venv name_of_venv
```

Activating a virtual environment:
```
$ source name_of_venv/Scripts/activate
```

Making sure VScode loads the correct virtual environment:
- Left click "Python 3.8" in the bottom left
- Click "+ Enter interpreter path"
- Click "Find"
- Go into your newly created virtual environment
- Select "Scripts"
- Select "python.exe"


Deactivating a virtual environment:
```
$ deactivate
```

Deleting a virtual environment:
[ Just delete the folder ]

## pip (Python package manager)

Install a package (i.e. flask):
```
$ pip install flask
```
(there *might* be some missing dependencies, so you might have to do pip install colorama and then pip install itsdangerous as well)

Creating/updating the requirements file (the list of everything installed):
```
$ pip freeze > requirements.txt
```

Installing everything from the requirements file:
```
$ pip install -r requirements.txt
```

Uninstalling packages (i.e. flask):
```
$ pip uninstall flask
```

## Running the flask server
Activating the flask server:
```
$ flask run
```

Load the page
[ Ctrl + click on the link shown in the terminal ]


Deactivate/kill the server:
[ Ctrl + C ]

## Routing
- url_for
- redirect(url_for())

## SECRET_KEY
(needed for form submission)

Generate
```
$ python
>>> import os
>>> os.urandom(24).hex()
```

Store (in __init__.py)
```python
app.config['SECRET_KEY'] = 'the-newly-generated-key'
```

## Templating/Jinja2

{% logic %}
{{ variables }}

https://jinja.palletsprojects.com/en/3.0.x/

## wsgi.py

The wsgi.py file sits in the root directory and redirects into the main app's folder:

```python
from name_of_your_app_folder import app

if __name__ == '__main__':
    app.run(debug=True)
```

## __init__.py

This tends to always have the following:

```python
from flask import Flask

app = Flask(__name__)

```

## Misc
__name__
https://www.freecodecamp.org/news/whats-in-a-python-s-name-506262fe61e8/