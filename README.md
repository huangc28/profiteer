## Profiteer

Backend archetect with `php 7.1`, `nginx`, `postgresql 9.6` and `redis`.

## Installation

Follow the steps below to properly run development environment.

Install docker on [mac](https://docs.docker.com/docker-for-mac/install/)

Install docker on [windows](https://docs.docker.com/docker-for-windows/install/)

## Execute commands in Container

`develop.sh` script made easier for developer to execute commands inside the docker container. For example `php artisan`, `composer`, `phpunit` ...etc

1. `./develop.sh art` ---> `php artisan`

2. `./develop.sh composer` ---> `composer`

3. `./develop.sh test` ---> `./vendor/bin/phpunit`

## Build the environment

`docker-composer up -d`. Open your browser, request `localhost:3001`.

## ERP Application

Create `application` folder, Place all server side code (in this case we use lumen) in `application` folder.

## Remark

- Nginx will be hosted on port `80` from the container, bridged by port `3001` on the host.
- Postgres will be hosted on port `5432` from the container, bridged by port `5432` on the host.