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

## Running the migrations

1. Run `docker compose up` to spin up the postgres database AND run `flyway migrate`.
1. Run `docker compose up -d flyway` to only run `flyway migrate` against an already running Postgres Docker container

## Running other Flyway commands in manual mode

1. If you don't want to automatically run `migrate` and maybe you want to play with some other commands, run `docker compose -f docker-compose-manual.yml up -d` and then run `docker exec -it flyway-manual /bin/sh`
