Data Containers
===================

Your application lives only if containers remain alive. If you want to make data
storage persistent use data-only containers.

How? Nothing change here:

```
docker-compose up -d
```

## docker-compose.yml
```
version: '2'

services:
  datadb:
    image: drupaldocker/mariadb
    entrypoint: /bin/true
  db:
    image: drupaldocker/mariadb
    environment:
      MYSQL_ALLOW_EMPTY_PASSWORD: 'True'
    volumes_from:
      - datadb
  dataapp:
    image: drupaldocker/php:apache
    entrypoint: /bin/true
  app:
    image: drupaldocker/php:apache
    links:
      - db
    ports:
      - 80
    volumes_from:
      - dataapp
```
