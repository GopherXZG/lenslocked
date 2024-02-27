# Postgres Data Types

<!--
  Branch: postgres-data-types
-->

Types provide a way to define what kind of data you want to store in a column. For example, you might say "I only want to store integers in this column" or "I only want to store strings that are smaller than 140 characters in this column".

PostgreSQL supports a [wide variety of data types](https://www.postgresql.org/docs/current/static/datatype.html), but in this course we will only need to use a handful of them. Below are a few common data types:

| Type  | Description|
| ----  | ---------- |
| `int` | This is used to store integers between -2147483648 and 2147483647. |
| `serial` | This is used to store integers between 1 and 2147483647. The big difference between `int` and `serial` is that serial will automatically set a value if you don't provide one, and the new value will always increase by 1. This is useful for things like the `id` column, where you want every row to have a unique value and are okay with the database deciding what value to use. |
| `varchar` | This is like a string in Go or other programming languages, except we have to tell the database what the max length of any string we are storing is going to be. |
| `text` | This is a type that is specific to PostgreSQL (and may not be available in all forms of SQL) but it is basically the same as `varchar` under the hood, but you don't have to specify a maximum string length when you declare your field. |

In Postgres I generally prefer `text` over `varchar`, but I mention both because `text` is specific to Postgres and `varchar` is not.
