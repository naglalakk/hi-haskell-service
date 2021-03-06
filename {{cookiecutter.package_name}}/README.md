{{ cookiecutter.package_name }}
===

### Installation

    -- configure and build
    cabal configure && cabal build

    -- run API. defaults to port :8081
    cabal exec {{ cookiecutter.package_name }} run

### Commands

**run**

Run API server. Optional port number
    
    run [-p|--port] 
    
**createuser**

Create a user. If the -a --admin flag is present
a API key is created and can be used for API
POST / DELETE methods.

    createuser (-u|--username ARG) (-p|--password ARG)
               [-e|--email ARG] [-a|--admin]


### Building with nix

    nix-build release.nix

### THINGS TO NOTE

The static path is static/uploads. This folder is omitted
from the repository since we don't want to store arbitrary
static files within the repo. When first running this project
you must create this folder if you want the upload to work properly. 
At the root of this project simply do

    mkdir static/uploads

Additionally you need to create a folder for the log files, used in production

    mkdir logs

### Env variables

Environment variables can be stored at the root of this project in a .env file. The current env variables used by this service are the following

**ENV**

Current environment. The options are

- Development
- Production

Switching these environments mostly changes how logging is managed

**PORTNR**

The port number for the service to run on. 

**PGHOST**

Postgres host (e.g. localhost)

**PGPORT**

Postgres port

**PGUSER**

Postgres username

**PGPASS**

Postgres password

**PGDATABASE**

Postgres database

**ES_URL**

Elasticsearch URL (default: localhost:9200)

**REDIS_HOST**

Redis host (default: localhost)

**SENTRY_URL**

SENTRY DNS URL to handle exceptions.
