# Docker Compose FTW!

Orchestrate your containers with drupal-compose.

## Description

Sometimes setting up environment can take a while even if we're using Docker.
Docker has nice tool which helps you manage your multi-container application -
docker-compose. docker-compose is a small command-line tool which reads
configuration stored in YAML file (docker-compose.yml) and builds your
application based on it.

## Prerequistes

Examples are written using compose version 2. Version 2 files are supported by Compose 1.6.0+ and require a Docker Engine of version 1.10.0+. Get most recent version of Docker Engine and [Docker Compose](https://docs.docker.com/compose/install/) from docker.com

## Available examples:

In this chapter you'll find a few examples how to start orchestrate your multi-container app with docker-compose.

1. Simple - MariaDB + php:apache
1. Data containers - Data Volume Containers
1. Drush - run drush container on demand
1. Networks - link containers with networks
