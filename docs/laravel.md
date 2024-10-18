# Laravel


The Laravel application would live under the __working_laravel__ directory, which is going to be a separate directory from any other PHP application.

## Installing a fresh Laravel application

Assuming that there are no other tools, tech stacks etc installed locally except from Docker, to install a fresh Laravel application we will need to do it using the [Composer's official image](https://hub.docker.com/_/composer). 

To install a fresh Laravel app inside the _working_laravel_ folder run this command
```
docker run --rm --interactive --tty --volume $PWD:/app composer create-project laravel/laravel working_laravel
```


## Running Laravel commands through the terminal

In order to run any Laravel commands, like artisan commands, or even composer commands, you can do it do it - either - by ssh-ing to the _php_ running container using the command right below and run the command you want inside the working directory.
```
docker compose exec php /bin/sh/
```

**However!** There's a better way: you can do it by using the _artisan_ and _composer_ services listed in the docker-compose.yml file.

So, to run any Composer commands you can do it like this
```
docker compose run --rm composer require laravel/breeze     // install Laravel Breeze
docker compose run --rm composer require laravel/breeze:"^1.26" // install a specific version
docker compose run --rm composer update     // update composer packages
```

Likewise for Artisan commands you can run them like this
```
docker compose run --rm artisan migrate
docker compose run --rm artisan make:model -fms FooModel
docker compose run --rm artisan make:contoller FooController
```

Likewise to run any npm commands you will do it using the _npm_ service
```
docker compose run --rm npm install
docker compose run --rm npm run dev
docker compose run --rm npm run build
```

[Go back](../README.md)