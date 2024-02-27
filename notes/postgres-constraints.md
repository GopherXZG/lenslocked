# Postgres Constraints

<!--
  Branch: postgres-constraints
-->

Example SQL:

```sql
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  age INT,
  first_name TEXT,
  last_name TEXT,
  email TEXT UNIQUE NOT NULL
);
```

Constraints are rules that we can apply to fields in our table. For example, we might want to ensure that every user in our database has a unique `id`, so we could use the `UNIQUE` constraint.

Like data types, there are [many constraints available in Postgres](https://www.postgresql.org/docs/current/static/ddl-constraints.html) but for now we will mostly be using the following.

| Constraint | Description |
| ---------- | ----------- |
| `UNIQUE` | This ensures that every record in your database has a unique value for the field that is set to unique. For example, you might want every user to have a unique email address. It is important to note that Postgres **is** case sensitive, so `jon@CALHOUN.io` is not the same as `jon@calhoun.io`. You will need to account for this on your own when writing data to your database. |
| `NOT NULL` | This ensure that every record in your database has a value for this field. When you don't provide a value for a field the database will traditionally store `null`, but this prevents that from being valid. |
| `PRIMARY KEY` | This constraint is similar to combining both `UNIQUE` and `NOT NULL` but it can only be used once on each table, and it will automatically result in a the creation of an index for this field. The index is used to make it faster to look up records by this field. For example, we typically set the `id` to be the primary key, and then we look up users by their id when we need to fetch them from the database. |

While it is common to check constraints like these in your own code, it is a good idea to set them up in the database to avoid race conditions.

For instance, if a user accidentally submitted a signup form twice it is possible for your code to process both forms at the same time and each might think the email address is unique and proceed with creating a user, resulting in two users with the same email address. On the other hand, if you had constraints setup on your database one of the two submissions would fail at the database level because the email address was inserted into the database.

In short, it is important to use database level constraints.
