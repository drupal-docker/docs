# CHANGELOG

Below you can find complete list of changes to images, sorted by date.

## 04-07-2018

General changes to `php` image:
- branch `2.x` became the default branch
- latest branch has been removed to encourage people do pull explicit php version
- branch `master` became `1.x`
- branch `1.x` is no longer supported

Changes to `php:2.x`:
- VOLUME instruction has been removed. Developers must explicitly decide upon defining volume on container runtime
- All images are now alpine-based

## 15-06-2017
- Drush 8 and Drush 9 (master) are now based on [PHP7 cli image](https://github.com/drupal-docker/php/blob/master/7.0/Dockerfile-cli)

## 05-05-2017
- On **June 5, 2017** PHP version for Drush 8 and master will be bumped from 5.6 to 7.0

## 22-03-2017
- Most image tags for php images are now deprecated. It is recommended to use minor version tag of your need, i.e. 5.6-fpm or 7.1-fpm, etc.

## 13-09-2016

- Dropping support for drupaldocker/php:5.5 (all tags) by **Dec 13, 2016**
- Dropping support for drupaldocker/php:5.4 (all tags) by **Dec 13, 2016**
