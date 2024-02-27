# Create users table

Putting this all together, we are going to create a `users` table.

There is a good chance you created a `users` table already, so let's first drop it.

```sql
DROP TABLE IF EXISTS users;
```

This will drop the users table if it exists.

Next run the following code which uses some of the types and constraints we learned about earlier.

```sql
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  age INT,
  first_name TEXT,
  last_name TEXT,
  email TEXT UNIQUE NOT NULL
);
```

You should see the output `CREATE TABLE`. If you instead see `ERROR:  relation "users" already exists` that means you already created a users table. To remove the table and recreate it you would need to run the `DROP TABLE` bit we did earlier in this lesson.
