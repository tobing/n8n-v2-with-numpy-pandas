# n8n v2 with numpy and pandas

n8n v2 with separate task runner and worker. Integrate with PostgreSQL and Redis.

Rebuild task runner with numpy and pandas using Dockerfile and also enable blocked nodes with ```NODES_EXCLUDE="[]"```

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

Verify if n8n, worker and task runner images are the same version:

```
docker inspect n8n-main n8n-worker n8n-custom-runner | grep image.version
```
To access it, open with web browser:
```
http://localhost:5678
```


## Configuration

The default name of the database, user and password for PostgreSQL and also n8n version can be changed in the [`.env`](.env) file in the current directory.

Packages for task runner can be modified with ```Dockerfile``` and ```n8n-task-runners.json``` inside [`n8n-custom-runner`](n8n-custom-runner)
