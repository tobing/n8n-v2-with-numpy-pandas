# n8n v2 with numpy and pandas

n8n v2 with separate task runner and worker. Integrate with PostgreSQL and Redis.

Rebuild task runner with numpy and pandas using Dockerfile and also enable some blocked node with ```NODES_EXCLUDE="[]"```

## Start

To start n8n simply start docker-compose by executing the following
command in the current folder.

**IMPORTANT:** Change the default users and passwords in the [`.env`](.env) file!

```
docker compose up -d --build
```

To stop it execute:

```
docker-compose stop
```

## Configuration

The default name of the database, user and password for PostgreSQL and n8n version can be changed in the [`.env`](.env) file in the current directory.
