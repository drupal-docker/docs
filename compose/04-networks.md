Networks
=================

Ok, you have multi-container app now, and you know how to link containers together.
But we should remember container has to be up&running to link them one to another. 
What if your db container crash? Unfortunately, you would have to rebuild php as well.

## Networks for the rescue!

Docker introduce networking tool which took over linking functionality.
You can create networks and add containers to those networks so they can connect
each other. Let's build simple app with two networks:

- back-tier
- front-tier

First one groups all containers vital for our application, like php and db,
while second one contain only containers which are relevant for exposing app to
the outside world.

You can build your application as always:
```
docker-compose up -d
```

You can still run drush on demand:
```
docker-compose run --rm drush bash
```

## docker-compose.yml
```yaml
version: '3.5'

services:
  db:
    image: drupaldocker/mariadb:10.3
    environment:
      MYSQL_ALLOW_EMPTY_PASSWORD: 'True'
    volumes:
      - db_volume:/var/lib/mysql
    networks:
      - back-tier
  php:
    image: drupaldocker/php:7.0-fpm-2.x
    volumes:
      - file_volume:/var/www/html
    networks:
      - back-tier
      - front-tier
  web:
    image: drupaldocker/nginx:1.13-2.x
    ports:
      - 80
    volumes:
      - file_volume:/var/www/html
    networks:
      - front-tier
  drush:
    image: drupaldocker/drush:8
    networks:
      - back-tier
    volumes:
      - file_volume:/var/www/html

volumes:
  db_volume:
  file_volume:

networks:
  front-tier:
  back-tier:
  ```
