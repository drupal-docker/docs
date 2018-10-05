Drush
=================

Ok, so you have mysql, php, apache but you'd like to use your favorite Drupal
command-line tool - Drush?

Just run your app:

```
docker-compose up -d
```

then run Drush service:

```
docker-compose --rm run drush
```

Now you have access to Drush interactive shell. Type `st` to see status of your
Drupal site. Press `Alt + D` to quit.

You can run as many Drush containers as you want. If you quit it will be
automatically destroyed. If you'd like to preserve your Drush container after it quits just
remove `--rm` flag from command.

```
docker-compose run drush
```

If you'd rather use Bash (with additional access to Drush command):

```
$ docker-compose --rm run drush bash
# drush st
```

You can quit at any time (just type `exit`).

***Be aware that /var/www/html volume you share across all app containers (php,
nginx, drush) so all changes that have been made to that directory will
affect other containers as well.***

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
  php:
    image: drupaldocker/php:7.0-fpm-2.x
    links:
      - db
    volumes:
      - file_volume:/var/www/html
  nginx:
    image: drupaldocker/nginx:1.13-2.x
    links:
      - php
    ports:
      - 80
    volumes:
      - file_volume:/var/www/html
  drush:
    image: drupaldocker/drush:8
    links:
      - db
    volumes:
      - file_volume:/var/www/html

volumes:
  db_volume:
  file_volume:

```
