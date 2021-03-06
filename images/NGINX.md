# NGINX

> Nginx (pronounced "engine-x") is an open source reverse proxy server for HTTP, HTTPS, SMTP, POP3, and IMAP protocols, as well as a load balancer, HTTP cache, and a web server (origin server). The nginx project started with a strong focus on high concurrency, high performance and low memory usage. It is licensed under the 2-clause BSD-like license and it runs on Linux, BSD variants, Mac OS X, Solaris, AIX, HP-UX, as well as on other *nix flavors. It also has a proof of concept port for Microsoft Window..

> source: [nginx](https://hub.docker.com/_/nginx/)

## Links

[Docker Hub](https://hub.docker.com/r/drupaldocker/nginx)
[GitHub](https://github.com/drupal-docker/nginx)

## Quickstart

```bash
docker run -d -p 80:80 --volumes-from <php-or-data-container> --link <php-fpm-container>:php drupaldocker/nginx
```

## Environmental variables

- `DOCROOT`: `/var/www/html` (default)
- `SERVER_NAME`: `_` (default)
