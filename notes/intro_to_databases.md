

## Setting up
In __init__.py file:

```python
app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///my_db_name.db"
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
