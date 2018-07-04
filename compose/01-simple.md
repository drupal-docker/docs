Simple
=============

Running MySQL + PHP + Apache is as simply as typing:
```
docker-compose up -d
```

## docker-compose.yml
```
version: '3.5'

services:
  db:
    image: drupaldocker/mariadb:10.3
    environment:
      MYSQL_ALLOW_EMPTY_PASSWORD: 'True'
  app:
    image: drupaldocker/php:7.0-apache-1.x
    links:
      - db
    ports:
      - 80
```
