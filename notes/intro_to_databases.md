
## Setting up

Requirements for your virtual environment
```
$ pip install flask-sqlalchemy
```

In __init__.py file:

```python
import os
from flask_sqlalchemy import SQLAlchemy

basedir = os.path.abspath(os.path.dirname(__file__))
app.config["SQLALCHEMY_DATABASE_URI"] = f"sqlite:///{os.path.join(basedir,'my_db.db')}"
```

Creating a simple database
(I use a file called db_maker.py placed in the root directory of the project - same directory as wsgi.py)

```
from name_of_my_app import db
from name_of_my_app.models import Users # basically import all models required by the database 

db.drop_all()
db.create_all()

user = User(name="testname") # let's assume that the only field required for a User is "name"

db.session.add(user)
db.session.commit()
```


## Relationships
### 

ONE to MANY relationships
```python
# PARENT to CHILD relationships
class OneParentTable(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(80))
    my_link_to_the_child_table = db.relationship("ManyChildTable", backref="backref_from_parent_table")

    def __repr__(self):
        return self.name

class ManyChildTable(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(80))
    foreign_key_to_one_parent_table = db.Column(db.Integer, db.ForeignKey("one_parent_table.id"))

    def __repr__(self):
        return self.name
```

ONE to ONE relationships
(same as one to many, just add ```uselist=False``` to the db.relationship)
```python
# PARENT to CHILD relationships
class OneParentTable(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(80))
    my_link_to_the_child_table = db.relationship("ManyChildTable", backref="backref_from_parent_table", uselist=False)

    def __repr__(self):
        return self.name

class ManyChildTable(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(80))
    foreign_key_to_one_parent_table = db.Column(db.Integer, db.ForeignKey("one_parent_table.id"))

    def __repr__(self):
        return self.name
```
