# Installing Postgres

Options:

1. Install Postgres directly. See <http://www.calhoun.io/using-postgresql-with-golang/>
2. Use Docker and `docker-compose`. See <https://docs.docker.com/get-docker/> to install Docker.

We will be using (2) because it is the same across all operating systems once you have Docker installed.

Docker is kinda like a way of spinning up virtual machines, but much more efficient.

(2) works because of the [Postgres Image](https://hub.docker.com/_/postgres) which is an image that loads up and runs a Postgres database when we run the image.

This means we can run a linux "VM" that has a Postgres database on it, and then connect to it from our computer. That is what we will be setting up in this lesson.


First, install docker - <https://docs.docker.com/get-docker/>

Second, verify it works in your terminal:

```bash
docker version
# you should see some version, not an error
docker-compose version
# again, output, not an error
```

Now create a `docker-compose.yml` file:

```bash
code docker-compose.yml
```

Add the following to it:

```yml
version: "3.9"

services:
  # Our Postgres database
  db: # The service will be named db.
    image: postgres # The postgres image will be used
    restart: always # Always try to restart if this stops running
    environment: # Provide environment variables
      POSTGRES_USER: baloo # POSTGRES_USER env var w/ value baloo
      POSTGRES_PASSWORD: junglebook
      POSTGRES_DB: lenslocked # Database name
    ports: # Expose ports so that apps not running via docker-compose can connect to them.
      - 5432:5432 # format here is "port on our machine":"port on container"

  # Adminer provides a nice little web UI to connect to databases
  adminer:
    image: adminer
    restart: always
    environment:
      ADMINER_DESIGN: dracula # Pick a theme - https://github.com/vrana/adminer/tree/master/designs
    ports:
      - 3333:8080
```

I've also included `adminer` which is a simple way to view our database, run some SQL queries in a browser, and do other dev-related tasks. We will see that in a moment.

In your browser head to <localhost:3333>

You should see Adminer loaded up. Choose the following options:

| **Option** | **Selection** |
| ---------- | ------------- |
| System     | Postgres      |
| Server     | db            |
| Username   | baloo         |
| Password   | junglebook    |
| Database   | lenslocked    |

You can check the permanent login option as well if you want.

_Note: The server option stems from us naming the service `db` in our `docker-compose.yml` file. If we were to rename it, we would need to use the updated value here. The same goes for most other options - they are derived from values in the docker-compose file, so if you change any you need to also use the updated values to log in._

If everything is working, you should be able to log in and see a dashboard. It will be pretty sparse until we start adding to our database, but this means we have everything working.

You can press `ctrl+c` to stop your `docker-compose`. You can also run `docker-compose down` to cleanup things and then when you run `docker-compose up` things should be in a fresh state.

We can also use the `-d` flag to run in detached mode, which will be in the background. Docker may automatically start your service up if you reboot, and if so it will be running in a mode like this. Stopping it is easy with `docker-compose down`
