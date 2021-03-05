0) install Lando globally

1) install drupal project in root folder
composer create-project drupal/recommended-project:9.1.4 .


2) make a file in root folder - .lando.yml
//**
recipe: drupal9
config:
  php: '7.4'
  composer_version: 1.10.20
  via: 'apache:2.4'
  webroot: web
  database: 'mysql:5.7'
  drush: ^10
  xdebug: true
services:
  pma:
    type: phpmyadmin
    hosts:
      - database
    portforward: 1026
  node:
    type: 'node:14'
    build:
      - cd /app && npm install & npm install -g gulp-cli
tooling:
  npm:
    service: node
  node:
    service: node
  gulp:
    service: node
  yarn:
    service: node
name: your name project
**//
3) run command - lando init

-> select - current working directory
-> select - drupal9
-> enter - web

4) Enter your project name - Project Name

5) run command - lando start

6) run command - lando composer install

7) run command - lando composer require drush/drush

8) in install process fill the fields with next data:

-> DB name - drupal9
-> DB username - drupal9
-> DB password - drupal9

Advanced Options:

-> host - database
