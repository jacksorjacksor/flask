# Intro to Forms

Forms let the user submit input to the Python framework. The Python framework can then send back the results. These can be in many types, including strings/ints/floats, lists and dictionaries

## Prerequisites
venv, with following packages:
- flask
- flask-wtf (installed with Flask-WTF)

__init__.py file has a secret key (see SECRET_KEY in "concepts_and_snippets.md")

## forms.py
Where the form is defined

```python
from flask_wtf import FlaskForm
from wtforms import StringField, SubmitField 

class MyForm(FlaskForm):
    user_input = StringField(label="Please enter a string")
    submit_button = SubmitField(label="Enter")
```

## routes.py
Where the Python logic will be stored 

```python
from my_app import app # this refers to the contents of __init__.py
from my_app.forms import MyForm

@app.route("/", methods=["GET", "POST"])
def home_function():
    form = MyForm()
    if form.validate_on_submit():
        output_result = form.user_input.data 
    else:
        output_result = None
    return render_template("template.html", form=form, output_result=output_result)
```

## template.html
What the user sees. This allows them to input data and will be how the output will be displayed. 

```html
<head></head>
<body>
<form method="POST" action="">
    <p>{{ form.csrf_token }}</p>
    <p>{{ form.user_input.label }} {{ form.user_input }}</p>
    <p>{{ form.submit_button }}</p>

</form>
{% if output_result %}
    <h2>You entered: {{ output_result }}</h2>
{% endif %}
</body>
```