# Intro to Databases

Our app doesn't persist data. Not very interesting. ☹️

Technically we could use almost anything to persist data. We could simply open up a text file in our code and write data to it.

```
# users.csv
jon calhoun, jon@calhoun.io, pw-hash, ...
Lauren Smith, laurensmith@gmail.com, dif-pw-hash, ...
...
```

Text files won't work well in the long run.

- The don't scale well
- Race conditions are possible
- Plus many more issues

We would need to invent all sorts of mechanisms to make them work, and we would basically be reinventing a database.

Rather than creating our own database, we are going to use an existing option.

There are many types of databases, all designed for different situations:

- Relational Databases - PostgreSQL & MySQL
- Document Stores - MongoDB
- Graph Databases - Dgraph & Neo4j
- Key/value stores - BoltDB, etcd

Each DB has pros and cons. If a DB is great at one thing, it is making a tradeoff somewhere else. As a result, most large companies use a variety of databases for different tasks.

We will be using PostgreSQL, which is:

- Very popular
- Free & open source
- Scales very well
- Not overly complex
- Well supported in Go
- Transactions to prevent race conditions
- Great all around option. Only bad in very hyper specific cases.

Don't believe anyone who says relational DBs are an ancient relic. See [Relational Databases Aren’t Dinosaurs, They’re Sharks](https://www.simplethread.com/relational-databases-arent-dinosaurs-theyre-sharks/).

Relational databases are widely used b/c they work extremely well for web apps.

The rest of this section is going to be a crash course on...
- Running Postgres via Docker
- Interacting with Postgres
- Learning a bit about how Postgres works

I will try to explain every query we make in this course, but it may be beneficial to learn more about SQL on your own after finishing the course.

No need to stop and go learn it all now - I'd suggest following along first.
