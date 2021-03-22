---
title: "Sqlite3 With Python"
date: 2021-03-20T09:11:50-03:00
draft: true
---

## Connection

First, we need to create a connection with database:
```python
import sqlite3
from sqlite3 import Error

def create_connection(db_file):
  '''Create a database conection to a SQLite databse'''

  conn = None

  try:
    conn = sqlite3.connect(db_file)
    print(sqlite3.version)
  except Error as e:
    print(e)
  finally:
    if conn:
    conn.close()
```

To create a connection, it's needed to invoke the function `connect()` from `sqlite3`, and save it in a variable.
In this case the connection was saved in `conn`, this variable will recieve all the queries.

After running this on python3 interactive shell we will receive the version of sqlite library and the databse will be generated:

`$ python3`
```
>>> from create_connection import create_connection
>>> create_connection('my_database.db')
2.6.0
>>>
```

![image 1](screenshot_1.png)

If you pass file name as ':memory:', the database will be saved on the memory of computer:

![image 2](screenshot_2.png)


## Refactor

Before of all, lets create a class where will contain all the methods:

`db_manager.py`
```python
class DB_Manager:
  def __init__(self):
    self.conn = None

  def create_connection(self, db_file="database.db"):
    try:
      self.conn = sqlite3.connect(db_file)
    except Error as e:
      print(e)
```

## Create tables

let's add the function `create_table()` to the class:

```python
def create_table(self, create_table_sql):
  """ create a table from the create_table_sql statement
  :param conn: Connection object
  :param create_table_sql: a CREATE TABLE statement
  :return:
  """

  try:
    c = self.conn.cursor()
    c.execute(create_table_sql)
  except Error as e:
    print(e)

```

With the `DB_Manager`, let's run the Python Interactive Shell:
```bash
$ python3
```

Let's import the `DB_Manager`:
```python
>>> from db_manager import DB_manager
```
then declare the variable containing the database name:
```python
>>> database = 'pythonsqlite.db'
```
then, declare the variable containing the SQL statement of project table and the task table:
```python
>>> sql_create_projects_table = """ CREATE TABLE IF NOT EXISTS projects (
                                      id integer PRIMARY KEY,
                                      name text NOT NULL,
                                      begin_date text,
                                      end_date text
                                    ); """
>>> sql_create_tasks_table = """ CREATE TABLE IF NOT EXISTS tasks (
                                  id integer PRIMARY KEY,
                                  name text NOT NULL,
                                  priority integer,
                                  status_id integer NOT NULL,
                                  project_id integer NOT NULL,
                                  begin_date text NOT NULL,
                                  end_date text NOT NULL,
                                  FOREIGN KEY (project_id) REFERENCES projects (id)
                                ); """
```
then, we will instantiate the `DB_Manager` and create the connection:
```python
>>> db_manager = DB_Manager()
>>> db_manager.create_connection()
```

after, let's create the tables:
```python
>>> if db_manager.conn is not None:
        # create projects table
        db_manager.create_table(sql_create_projects_table)

        # create tasks table
        db_manager.create_table(sql_create_tasks_table)
    else:
        print("Error! cannot create the database connection.")
```

If we run `ls` we will see that `database.db` was created:

![screenshot 3](screenshot_3.png)

Now we can use the command `sqlite3` passing our database as a param, then, run the `.tables` command to see the tables that we created:

![screenshot 4](screenshot_4.png)

---
## referencies:

SQLite Python: [_https://www.sqlitetutorial.net/sqlite-python/_](https://www.sqlitetutorial.net/sqlite-python/)
  - Creating a New Database: [_https://www.sqlitetutorial.net/sqlite-python/creating-database/_](https://www.sqlitetutorial.net/sqlite-python/creating-database/)
  - Creating Tables: [_https://www.sqlitetutorial.net/sqlite-python/create-tables/_](https://www.sqlitetutorial.net/sqlite-python/create-tables/)
