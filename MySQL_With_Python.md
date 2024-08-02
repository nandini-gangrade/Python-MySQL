
# Quick Guide to Using MySQL Database with Python

Hello everyone, I hope you are doing well.

Today, I am here with a quick guide on how to use the MySQL database with Python. Here I will describe everything which is required to use the MySQL database with Python. As we all know, MySQL is a widely-used database and Python supports MySQL databases.

To get started with Python MySQL, we need to install a MySQL connector for Python. For that, open your terminal, and run the following command.

```
python -m pip install mysql-connector-python
```

It will install the required MySQL driver for Python and no MySQL connector is available and ready to use. Now we need to create a connection with the correct parameters.

## Table of Contents

1. [Create Connection](#create-connection)
2. [Create a Table](#create-a-table)
3. [Insert Data into the Table](#insert-data-into-the-table)
4. [Select Data from the Table](#select-data-from-the-table)
    - [Select all records](#select-all-records)
    - [Select with where clause](#select-with-where-clause)
    - [Select and order by](#select-and-order-by)
    - [Select with the limit](#select-with-the-limit)
5. [Delete Record from Table](#delete-record-from-table)
6. [Update a Record in the Table](#update-a-record-in-the-table)
7. [Drop Table](#drop-table)
8. [Summary](#summary)

## Create Connection

To create a connection with the MySQL database, first we need to import the MySQL connector and then execute the MySQL connect method with valid credentials such as database username, password, database name, and database host. Check the following code:

```python
import mysql.connector

mydb = mysql.connector.connect(
    host="localhost",
    user="username",
    password="password",
    database="database"
)

mycursor = mydb.cursor()
```

## Create a Table

To create a table in the current database, use the following syntax:

```python
# Note: import mysql connector and create mysql connection

mycursor = mydb.cursor()
mycursor.execute("CREATE TABLE posts (id INT NOT NULL AUTO_INCREMENT COMMENT 'primary key', title VARCHAR(255), description TEXT)")
```

It will create a new table with the name `posts`.

## Insert Data into the Table

To insert a new record into the table, use the following command:

```python
# Note: import mysql connector and create mysql connection

mycursor = mydb.cursor()
sql = "INSERT INTO posts (title, description) VALUES (%s, %s)"
val = ("This is my post title", "HI, it is awesome")
mycursor.execute(sql, val)
mydb.commit()

print(mycursor.rowcount, "record has been inserted successfully.")
```

## Select Data from the Table

### Select All Records

Select all records from the posts table and show them.

```python
# Note: import mysql connector and create mysql connection

mycursor = mydb.cursor()
mycursor.execute("SELECT * FROM posts")
posts = mycursor.fetchall()

for x in posts:
    print(x)
```

### Select with Where Clause

Select records from posts table where id is > 10

```python
# Note: import mysql connector and create mysql connection

mycursor = mydb.cursor()
sql = "SELECT * FROM posts WHERE id > 10"
mycursor.execute(sql)
posts = mycursor.fetchall()

for x in posts:
    print(x)
```

### Select and Order By

Select all records from posts and order them by id in descending order.

```python
# Note: import mysql connector and create mysql connection

mycursor = mydb.cursor()
sql = "SELECT * FROM posts ORDER BY id DESC"
mycursor.execute(sql)
posts = mycursor.fetchall()

for x in posts:
    print(x)
```

### Select with the Limit

Select 5 records from posts:

```python
# Note: import mysql connector and create mysql connection

mycursor = mydb.cursor()
sql = "SELECT * FROM posts LIMIT 5"
mycursor.execute(sql)
posts = mycursor.fetchall()

for x in posts:
    print(x)
```

## Delete Record from Table

Delete post with id = 10

```python
# Note: import mysql connector and create mysql connection

mycursor = mydb.cursor()
sql = "DELETE FROM posts WHERE id = 10"
mycursor.execute(sql)
mydb.commit()

print(mycursor.rowcount, "post has been deleted successfully.")
```

## Update a Record in the Table

Change the description of the post with id = 10.

```python
# Note: import mysql connector and create mysql connection

mycursor = mydb.cursor()
sql = "UPDATE posts SET description = 'Description has been changed.' WHERE id = 10"
mycursor.execute(sql)
mydb.commit()

print(mycursor.rowcount, "record(s) affected")
```

## Drop Table

Drop posts table from the database if it exists.

```python
# Note: import mysql connector and create mysql connection

mycursor = mydb.cursor()
sql = "DROP TABLE IF EXISTS posts"
mycursor.execute(sql)
```

## Summary

In this post, I have covered all basic operations to get started with the MySQL database with Python. I have answered some of the most common questions such as how to install the Python MySQL connector, how to create a table with Python MySQL, how to select, update, and delete records from tables with Python MySQL, etc. I hope you will like this quick start guide to Python MySQL.

If you love reading this post, please follow me for more posts like this. Thank you in advance.
