# Docker for Laravel

Minimalist docker container to run a Laravel project with php7.2-fpm, nginx and mysql-5.7 with xdebug support.

## Getting started

This container was created to have a minimalist and easy-to-run docker container for laravel applications. 

### Prerequisites

Before using this docker container, you should be sure to have Docker already installed on your system. Also, you need to install composer to create your Laravel project.

### Installing

Clone this repository inside your Laravel's project folder (or one level above).

```
git clone https://github.com/deleonn/laravel-docker.git
```

Next, you need to edit `docker-compose.override.yml` to add your project path to both nginx and php volumes. This will sync your local code with docker.

```
[...]

nginx:
    volumes:
        - ./path/to/project:/var/www/laravel

php:
    volumes:
        - ./path/to/project:/var/www/laravel
```

An additional but not necessary step, you need to navigate to `images/nginx/vhost.conf` and replace the `server_name laravel.test;` with your own server name (remember that you need to modify your HOSTS to map 127.0.0.1 to your server_name to access your project from the browser).

Finally, replace mysql environment variables with your own configuration.

```
  environment:
    MYSQL_ROOT_PASSWORD: root_password
    MYSQL_DATABASE: my_database
    MYSQL_USER: my_user
    MYSQL_PASSWORD: my_password
```

To run your now dockerized laravel application, run `docker-compose up` to start your docker services (Additionally, you can use the `-d` flag to run docker at the background).

And that's it. Navigate to laravel.test to see your project running.

_Credits for this docker setup goes to (https://github.com/carloct)_.