# Laravel


The Laravel application would live under the __working_laravel__ directory, which is going to be a separate directory from any other PHP application.

## Installing a fresh Laravel application

Assuming that there are no other tools, tech stacks etc installed locally except from Docker, to install a fresh Laravel application we will need to do it using the [Composer's official image](https://hub.docker.com/_/composer). 

To install a fresh Laravel app inside the _working_laravel_ folder run this command
```
docker run --rm --interactive --tty --volume $PWD:/app composer create-project laravel/laravel working_laravel
```

[Go back](../README.md)