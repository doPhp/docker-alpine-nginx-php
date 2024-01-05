# Docker PHP-FPM 8.3 & Nginx on Alpine Linux 3.19

Based on the original work from [Trafex](https://github.com/TrafeX/docker-php-nginx), but moved on to support PHP-FPM 8.3 and be more forward moving on Alpine

## Goal of this project
The goal of this container image is to provide an example for running Nginx and PHP-FPM in a container which follows
the best practices and is easy to understand and modify to your needs.

## Usage

Start the Docker container:

```zsh
docker run -p 80:8080 trafex/php-nginx
```

See the PHP info on http://localhost, or the static html page on http://localhost/test.html

Or mount your own code to be served by PHP-FPM & Nginx

```zsh
docker run -p 80:8080 -v ~/my-codebase:/var/www/html trafex/php-nginx
```

## Configuration
In [config/](config/) you'll find the default configuration files for Nginx, PHP and PHP-FPM.
If you want to extend or customize that you can do so by mounting a configuration file in the correct folder;

Nginx configuration:

```zsh
docker run -v "`pwd`/nginx-server.conf:/etc/nginx/conf.d/server.conf" trafex/php-nginx
```

PHP configuration:

```zsh
docker run -v "`pwd`/php-setting.ini:/etc/php82/conf.d/settings.ini" trafex/php-nginx
```

PHP-FPM configuration:

```zsh
docker run -v "`pwd`/php-fpm-settings.conf:/etc/php82/php-fpm.d/server.conf" trafex/php-nginx
```

_Note; Because `-v` requires an absolute path I've added `pwd` in the example to return the absolute path to the current directory_

## Documentation and examples
To modify this container to your specific needs please see the following examples from Trafex;

* [Adding xdebug support](https://github.com/doPhp/docker-alpine-nginx-php/blob/master/docs/xdebug-support.md)
* [Adding composer](https://github.com/doPhp/docker-alpine-nginx-php/blob/master/docs/composer-support.md)
* [Getting the real IP of the client behind a load balancer](https://github.com/doPhp/docker-alpine-nginx-php/blob/master/docs/real-ip-behind-loadbalancer.md)
* [Sending e-mails](https://github.com/doPhp/docker-alpine-nginx-php/blob/master/docs/sending-emails.md)