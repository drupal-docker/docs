Drush
=================

Ok, so you have mysql, php, apache but you'd like to use your favorite drupal
command-line tool - drush?

Just run your app:

```
docker-compose up -d
```

then run drush service:

```
docker-compose --rm run drush
```

Now you have access to drush interactive shell. Type `st` to see status of your
Drupal site. Press `Alt + D` to quit.

You can run as many Drush containers as you want. If you quit it will be
automatically destroyed. If you'd like to preserve your Drush container just
remove `--rm` flag from command.

If you'd rather prefer to use Bash (with additional access to Drush command):

```
$ docker-compose --rm run drush bash
# drush st
```

You can quit at any time (just type `exit`).

***Be aware that /var/www/html volume you share across all app containers (php,
nginx, apache, drush) so all changes that have been made to that directory will
affect other containers as well.***

## docker-compose.yml
```yaml
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
  drush:
    image: drupaldocker/drush
    links:
      - db
    volumes_from:
      - dataapp
```
