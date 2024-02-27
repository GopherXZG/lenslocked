# Creating SQL Tables

<!--
  Branch: creating-sql-tables
  TODO: Add recap for how to psql into docker?
-->


Before we can store information in our database, we need to create a table that specifies what data we will be storing.

Tables are a little easier to understand if you think of them like a spreadsheet. In order to start storing data, we first need to create the spreadsheet and label each column.

![Sample spreadsheet for storing users.](/notes/users-spreadsheet.png)

Once we have a spreadsheet setup we can add data to it. Each row represents a new entry, and each column is a specific piece of information for that entry.

Let's look at an example of how we might create a database table similar to the spreadsheet example. Before we can create the table, we need to make sure we delete the users table we created earlier.

```sql
DROP TABLE IF EXISTS users;
```

This will tell Postgres to drop the `users` table if it exists. This is safe to run even if you never created the table.

Next we run the SQL query to create a table mapping to the spreadsheet we looked at.

```sql
CREATE TABLE users (
  id SERIAL,
  age INT,
  first_name TEXT,
  last_name TEXT,
  email TEXT
);
```

While the way we go about setting up a database table is a bit different, the end result is conceptually very similar. We are telling the database that for each user we want to store an `id`, `age`, `first_name`, `last_name`, and an `email`.

When we create an SQL table we will be using code that follows the format:

```sql
CREATE TABLE table_name (
  field_name TYPE CONSTRAINTS,
  field_name TYPE(args) CONSTRAINTS
);
```

We always declare the table name first, and then with each row we define a a field, or a column in the spreadsheet metaphor, and then we declare what type this field will be, followed by any constraints we have on the field.

Some types require additional arguments, which is why you will sometimes see parenthesis after the type with some values in it.

After the types we see the constraints. These are rules that we can set on each column that the database will enforce. We will discuss a few of these as we use them in the course.
