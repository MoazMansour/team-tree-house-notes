# Python peewee Module
- Peewee is a simple lightweight python ORM (Object Relational Mapping)
- ORM turn objects in your code into rows in your table.
- Models (ORM objects) has attributes which will become rows in your table

## Models:
- Models in peewee are python classes.
- Each attribute represents a column in the database
- Common convention for peewee is
    - ```from peewee import *```

### Create a database:
- e.g. `db = SqliteDatabase(‘students.db’)`
- Create a class which also has a convention. It has be singular like (Student) not (Students) that’s because a model represents one row in your table.
- This convention is very common for peewee and Django
- This class is derived from (Model)
- CharField equivalent to “VARCHAR”
- IntegerField Eq to “INT”
- max_length attribute works for VARCHAR(X)
- Unique attribute is a boolean to set a unique constraint
- Default attribute is how you set a default value for a row
- Add a Meta class under the model class.
- The meta class just tells the parent class which database it belongs to
- `db.connect()`: starts a connection with the database
- `db.create_tables([TABLE], safe=True)`
    - The safe attribute -> IF NOT EXISTS to avoid overriding and having creation errors

### Models Methods:
- `.create()`: creates a new row in the database
- `.select()`: fetchs rows from the db
- `.save()`: updates an existing row in the db
- `.get()`: fetch a single row from the table
- `.delete_instance()`: delete a row in a table

### Examples:
>**Class To be used:**
>
>     class Student(Model):
>         username = CharField(max_length=255, unique=True)
>         points = IntegerField(default=0)

>**Create a new record:**
>
>     Student.create(username="Moaz", points=147)

>**Update an existing record:**
>
>     student_record = Student.get(username="Moaz")
>     student_record.points = 145
>     student_record.save()

>**Select a record:**
>
>     student = Student.select()
>
> _Get them in order_
>
>     student = Student.select().order_by(Student.points.desc())
>
> _Get the top element_
>
>     student = Student.select().order_by(Student.points.desc()).get()

>**Filter in Query**
>
> This is equivalent to using WHERE statement in SQL
>
>     Student.select().order_by(Student.points.desc()).where(Student.content.contains(search_query))
>
>     Student.select().where(Student.name.contains(name), Student.points == points)

### CRUD:
- Create
- Read
- Update
- Delete

## Random Notes
- `content = TextField()` a peewee text field *no max max_length*
- `timestamp = DateTimeField(default=datetime.now)` no pranethesis so that whenever we are adding a row it would call the function and gets the new time. if there  was pranethesis it would have it set to whenever you started running the script
- common practice:
  - when importing different libraris into your script. Start with the stuff from python (default libraries) then a blank line then stuff that comes from the third party library

>**How to make python script executable for unix:**
>
>- If you have the shebang `#! /usr/bin/env python3` you can turn the python3 script to an executable file
>- change mood of the file to `chmod +x diary.py`
>- run the code with `./diary.py`

>**OrderDict From Collections library**
>
>- An alternative to switches in other languages
>- Dictionarioes hold options and their triggers
>- using OrderedDic keeps the optins in our dictionary in order
>- `from collections import OrderedDict`
>- explore named_tuples and counter from the collections library
>- The way we do this is by adding a list
>   - `menu = OrderedDict([('a', add_entry),('v', view_entries)])`
>-OrderDict act in the same exact way as a dictionary. The onlye difference that it keeps the order of the keys

>**Using __doc__**
>- what is `value.__doc__`
>- value is a function assigned to an option in our OrderedDict.
>- calling  `value.__doc__` will print out the docstring of this function

>**Using sys**
>
>capture everything the user type untill they enter EOF sequencing and that's by by pressing `ctrl+d` by the end of the sentence
>to capture their input we are gonna use `sys.stdin.read().strip()`

>**TimeStamp Format**
>
> - `%A`: Day of the week (Mon-Sat-etc)
> - `%B`: Name of the Month
> - `%d`: Day in the month
> - `%Y`: year
> - `%I`: Hour on 12-hour clock
> - `%M`: minute
> - `%p`: PM vs AM

>**Clear Screen**
>
> Using the `os` library you can clear the screen before printing something new to it.
>
> use `os.system('cls' if os.name == 'nt' else 'clear')`
>
> `nt` is used for windows OS while clear for unix/linux
