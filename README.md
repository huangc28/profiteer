## Profiteer

OS infrustructure for **nextdealshop ERP**. It's build up with `php 7.1`, `nginx`, `postgresql 9.6` and `redis`.

## Installation

Follow the steps below to properly run development environment.

Install docker on mac

`https://docs.docker.com/docker-for-mac/install/`

Install docker on windows

`https://docs.docker.com/docker-for-windows/install/`

Build the necessary images before building up the environment.

### Build php

Change directory to nginx,

`cd php`

and

`docker build -t nextdealshop/php .`

### Build nginx

Change directory to nginx

`cd ../nginx`

and

`docker build -t nextdealshop/nginx`

**nginx** will be hosted on port `80` from the container.

### Build postgres

Change directory to postgres

`cd ../postgres`


and

`docker build -t nextdealshop/postgres`

**postgres** will be hosted on port `5432` from the container

## Build the environment

`docker-composer up -d`. Open your browser, request `localhost:3001`.