## Creating Project dir

$ mkdir docker_symfony
$ cd docker_symfony
$ touch docker-compose.yml

$ docker -v

respsone will be
: Docker version ^version, build 48a66213fe

## Creating Container
    <=> Inside Docker-compose.yml 
1. For Mysql 
2. phpMyAdmin
3. MailDev

## Container For Apache & Php
$ mkdir php
$ cd php
$ touch Dockerfile

## Adding the project inside docker-compose
adding www: part 
    on docker-compose

## Build images 
$ docker-compose build

## Adding Vhosts
$ mkdir vhosts
$ cd vhosts
$ touch vhosts.conf

## Testing if all work & Starting docker
$ docker-compose up -d

## Adding php.ini in the project
$ cd php
$ touch php.ini

add the following lines into docker-compose => www: part

- ./build/php.ini:/usr/local/etc/php/php.ini

## Creating project symfony
$ docker exec www_docker_symfony \n
$ composer create-project symfony  \n
$ sudo chown -R $USER ./

## Config .env
DATABASE_URL=mysql://root:@db_docker_symfony:3306/db_name?serverVersion=5.7

## Creating Database from symfony Cli
$ docker exec -it www_docker_symfony bash
/var/www# php bin/console doctrine:database:create

## Creating Entity and so on... 
/var/www# php bin/console make:entity
/var/www# php bin/console make:migration
/var/www# php bin/console doctrine:migrations:migrate

## Config MAILER_DSN
MAILER_DSN=smtp://maildev_docker_symfony:25
