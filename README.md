# About

This repo shows a demo of using Flyway.

# Getting Started

## Prerequisites

1. Install Docker

## How it works

This project leverages Docker for a local environment so that you don't need to have Postgres installed on your machine. The `docker-compose.yml` file defines the container running the Postgres database with lines 3-9. It also defines the container that executes Flyway with lines 11-17. Of special note is the command being running with the Flyway container that specifies how to connect to the Docker container and also has the `migrate` command.

## Adding a new migration

1. Are you adding a versioned migration or a repeatable migration?

   1. If you're adding a new versioned migration (i.e. something one time such as adding a new table, adding a new column, running an `UPDATE` script, etc.), then add it to the `/sql/versioned` folder.
   1. If you're adding a new repeatable migration (i.e. something that should run every time it changes such as a stored procedure definition, view definition, etc.), then add it to the `/sql/repeatables` folder.

1. Add the migration to the correct folder above
1. Run `docker compose up` to run your migration against the Postgres database
