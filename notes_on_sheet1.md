# Notes on sheet 1

3. Literally no point in calling this "hello.py"
    - Extra confusion, just means you have to set/export FLASK_APP=hello - default is wsgi.py or app.py

4. Don't use:

```
$ flask run
```

Instead, run the base file (named "hello.py" in 3.) directly:

```
$ py hello.py # [ or wsgi.py or app.py - see my note above! ]
```

Fun note! If you add debug=True to the app instantiation, and use the python to run the file instead of "flask run" (as above), you never need to set any environment variables (i.e. 4a and 4b)

hello.py
```python
from flask import Flask

app = Flask(__name__, debug=True)

@app.route("")
def hello():
    return "Hello world!"
```

This can then be run with:

```
$ py hello.py
```

...and it'll be run in debug mode (which automatically tried to update when you make changes to your code). You don't need to set the variables at 4a or 4b, which you'd need to set EVERY TIME you load up VSCode.

6. Title variable not used despite being defined in 7.