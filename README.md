# DockerPratice
This simple Django/PostgreSQL app using Docker Compose

## Prerequisites

- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Development

Clone this repository

```
$ git clone https://github.com/jupiny/DockerPratice.git
$ cd DockerPratice/
```

Build the images and then start the services

```
$ docker-compose build
$ docker-compose up
```

## Production

Clone this repository

```
$ git clone https://github.com/jupiny/DockerPratice.git
$ cd DockerPratice/
```

Change port settings in `docker-compose.yml`

```
version: '2'
services:
  db:
    image: postgres
    # Add this setting!
    ports:
      - "5432:5432"
  web:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - "80:8000" # Enable to access port 80
    depends_on:
      - db
```

Builds the images and then start the services

```
$ docker-compose build
$ docker-compose up
```

## Reference

- [Quickstart: Docker Compose and Django](https://docs.docker.com/compose/django/)