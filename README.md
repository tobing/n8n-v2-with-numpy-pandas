> [!WARNING]
> Importing `pandas` in the Python Code node fails with a security violation in n8n 2.25+, stay in 2.23.4 for now. Issue has been submitted [Click here](https://github.com/n8n-io/n8n/issues/32149)


# n8n v2 with numpy and pandas

n8n v2 queue mode with separated task runner and worker. Integrated with PostgreSQL and Redis.

Rebuild task runner with numpy and pandas using Dockerfile and also enabled blocked nodes with ```NODES_EXCLUDE="[]"```

## Start

Clone this repo
```
git clone https://github.com/tobing/n8n-v2-with-numpy-pandas.git
cd n8n-v2-with-numpy-pandas
```

<br />


To start n8n simply start docker-compose by executing the following
command in the current folder.

**IMPORTANT:** Change the default users and passwords in the [`.env`](.env) file!

```
docker compose up -d --build
```

<br />

To stop it execute:

```
docker-compose stop
```

<br />

Verify if n8n, worker and task runner images are the same version:

```
docker inspect n8n-main n8n-worker n8n-custom-runner | grep image.version
```

<br />

To access it, open with web browser:
```
http://localhost:5678
```
For custom domain modify these lines in [`docker-compose.yaml`](docker-compose.yaml)

```
- VUE_APP_URL_BASE_API=http://localhost:5678/
- N8N_EDITOR_BASE_URL=http://localhost:5678/ 
- WEBHOOK_URL=http://localhost:5678/ 
```

<br />  

## Configuration

The default name of the database, user and password for PostgreSQL and also n8n version can be changed in the [`.env`](.env) file in the current directory.

External packages for task runner can be modified with ```Dockerfile``` and ```n8n-task-runners.json``` inside [`n8n-custom-runner`](n8n-custom-runner)

Task runner included these external packages:

**NODE**: ```moment,uuid,axios,cheerio,form-data,node-fetch,csv-parse```

**PYTHON**: ```numpy,pandas```

<br />

To verify the external packages working properly, import ```n8n-workflow.json``` from [`verify-external-modules`](verify-external-modules) to n8n then execute workflow.

The workflow has 3 nodes. Manual trigger, Node Modules Test and Python Modules Test.

