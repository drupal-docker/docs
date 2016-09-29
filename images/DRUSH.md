# Drush

> Drush is a command line shell and Unix scripting interface for Drupal. Drush core ships with lots of useful commands for interacting with code like modules/themes/profiles. Similarly, it runs update.php, executes sql queries and DB migrations, and misc utilities like run cron or clear cache. Drush can be extended by 3rd party commandfiles.

> source: [github](https://github.com/drush-ops/drush)

## Links

[Docker Hub](https://hub.docker.com/r/drupaldocker/drush)
[GitHub](https://github.com/drupal-docker/drush)

## Quickstart:

```bash
docker run --rm -ti --volumes-from <php> --link <mysql> drupaldocker/drush:8 /bin/bash
```

## Environmental variables

TBA
