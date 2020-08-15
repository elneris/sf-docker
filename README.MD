# Docker Symfony Project

### About me

- Elnéris Dang
- Web developper for Omnilog
- PHP / Symfony 

### About Project

- symfony 5.1
- PHP 7.4
- Apache 2.4
- PostgresSQL 12.0

### Requirements

Applications needed to work on this project :

- Any IDE (WebStorm, PHPStorm, Visual Basic, Atom, Vim, ...)
- Docker + Docker Compose
- A browser

### Installation

Change the file `.php_cs.dist` with your own information.

To install dependencies and to prepare environment, run the command below :

```
docker-compose build
```

This command will create images on your machine to allow you to run expected containers.

You have to run this command each time the `docker-compose.yml` file is updated.

### Start containers

To run the application, you have to execute the command below :

```
docker-compose up -d
```

The option `-d` is there to run docker containers in background and prevent it to lock the prompt.

This command will start 3 containers :

- sf-docker_apache_1
- sf_docker_db_1
- sf_docker_php_1

### Access to logs of the containers

If you need to have access to containers prompt or logs, you can run those commands :

```
docker-compose logs #container_name#
```

This command will replace your prompt by the one of the container. You can run the command below, if you need to have "live" logs, your prompt automatically linked to the container :

```
docker-compose logs -f #container_name#
```

### Enter into the container

If you need to execute commands into a container or need to access to file or inspect the container, you have to run the command below :

```
docker exec -it #container_name# bash
```

### Stop containers

When you finish to work or want to stop containers, you have to run this command :

```
docker-compose down
```

### Script to fix file & analyse code quality

Before your commit, run the command :

```
composer run check
``` 

This command will execute 3 things.

- "bin/console doctrine:schema:validate -n --skip-sync",
- "vendor/bin/php-cs-fixer fix",
- "vendor/bin/phpstan analyse src/ --level 4"

You can add your own rules by editing this script in `composer.json` under the `check` section
