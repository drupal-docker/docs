Simple
=============

Running MySQL + PHP + Apache is as simply as typing:
```
docker-compose up -d
```

## docker-compose.yml
```
version: '2'

services:
  db:
    image: drupaldocker/mariadb
    environment:
      MYSQL_ALLOW_EMPTY_PASSWORD: 'True'
  app:
    image: drupaldocker/php:apache
    links:
      - db
    ports:
      - 80
```
