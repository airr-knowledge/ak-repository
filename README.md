# AIRR Knowledge Repository

AIRR Knowledge is publicly accessible repository of data and knowledge about 1) adaptive immune
receptors (AIRs) and AIR repertoires, 2) the complex genomic loci encoding AIR genes, and 3) the
antigens and epitopes bound by AIR.

## Deployments

 * Production: https://airr-knowledge.org
 * Staging: https://ak-staging.airr-knowledge.org
 * Development: http://localhost

## Components

VDJServer Repository is currently composed of 2 separate components:

 * [ak-db]: Postgresql database.
 * [ak-web-api](https://github.com/airr-knowledge/ak-web-api.git): AIRR Knowledge Web API.
## Configuration Procedure

You will need to clone the parent project and all submodules in order to set up an instance of the AIRR Knowledge Repository.

```
# Clone project
$ git clone https://github.com/airr-knowledge/ak-repository.git

$ cd ak-repository

# Clone submodules
$ git submodule update --init --recursive
```

All configuration procedures are based upon docker containers of the components.

There is one configuration file that needs to be set up to run the
repository. It can be copied from its default template.

```
cp .env.defaults .env
pico .env
```

## Deployment Procedure

### SSL

### Docker compose build

There are a set of docker compose files for building and starting all of the components.

```
$ cd docker-compose/ak-db
$ docker compose build
```

If everything has build properly, then can manually bring up the system with:

```
$ docker compose up
```

Verify no unexpected error messages. Verify you can access the website GUI. Manually bring down the system with:

```
$ docker compose down
```

### Configuring systemd

### Running the test suites (staging, production)**

## Accessing the Repository

### ADC API

The top level entrypoint for the ADC API will return a simple success status heartbeat.

```
$ curl http://localhost:8050/akc/v1
{"result":"success"}
```

The info entrypoint will return version and other info about the service.

```
$ curl http://localhost:8050/akc/v1/info
{
  "title": "ak-api",
  "description": "AIRR Knowledge API Service",
  "version": "0.1.0",
  "contact": {
    "name": "AIRR Knowledge",
    "url": "http://airr-knowledge.org/",
    "email": "airr-knowledge@utsouthwestern.edu"
  },
  "license": {
    "name": "GNU AGPL V3"
  },
  "api": {
    "title": "AIRR Knowledge API",
    "version": "1.0.0",
    "contact": {
      "name": "AIRR Knowledge",
      "url": "https://airr-knowledge.org/",
      "email": "airr-knowledge@utsouthwestern.edu"
    },
    "description": "API service for AIRR Knowledge."
  },
  "max_query_size": 2097152
}
```
