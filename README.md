# PHP on Raspberry Pi / ARM

### NOT MAINTAINED AND DEPRECATED

This image is not maintained and is deprecated!  
  
Please use the following images:

* offical [php](https://hub.docker.com/_/php)-Images ([arm32v5](https://hub.docker.com/r/arm32v5/php/), [arm32v6](https://hub.docker.com/r/arm32v6/php/), [arm32v7](https://hub.docker.com/r/arm32v7/php/), [arm64v8](https://hub.docker.com/r/arm64v8/php/))
* [webhippie/php-cli](https://hub.docker.com/r/webhippie/php-cli)-Images or [webhippie/php-nginx](https://hub.docker.com/r/webhippie/php-nginx)-Images or [webhippie/php-apache](https://hub.docker.com/r/webhippie/php-apache)-Images
* or my php-Images based on offical php ([DockerHub](https://hub.docker.com/r/tobi312/php/)/[GitHub](https://github.com/Tob1asDocker/php)) or my alpine-nginx-php-Images ([DockerHub](https://hub.docker.com/r/tobi312/alpine-nginx-php/)/[GitHub](https://github.com/Tob1asDocker/alpine-nginx-php))

---

### Supported tags and respective `Dockerfile` links
-	[`7.0-fpm`, `latest` (*Dockerfile*)](https://github.com/TobiasH87Docker/rpi-php/blob/master/7.0-fpm/Dockerfile)
-	[`5.6-fpm` (*Dockerfile*)](https://github.com/TobiasH87Docker/rpi-php/blob/master/5.6-fpm/Dockerfile)

### What is PHP?

PHP is a server-side scripting language designed for web development, but which can also be used as a general-purpose programming language. PHP can be added to straight HTML or it can be used with a variety of templating engines and web frameworks. PHP code is usually processed by an interpreter, which is either implemented as a native module on the web-server or as a common gateway interface (CGI).
> [wikipedia.org/wiki/PHP](https://en.wikipedia.org/wiki/PHP) and [php.net](https://php.net)

![logo](https://raw.githubusercontent.com/docker-library/docs/master/php/logo.png)

### How to use this image
* ``` $ docker pull tobi312/rpi-php:5.6-fpm ```
* Optional: ``` $ mkdir -p /home/pi/html ```
* ``` $ docker run --name php --link some-sql-container:alias -v /home/pi/html:/var/www/html -e PHP_ERRORS=1 -e PHP_UPLOAD_MAX_FILESIZE=250 -d tobi312/rpi-php:5.6-fpm ``` 

or build it yourself
* ``` $ git clone https://github.com/Tob1asDocker/rpi-php.git && cd rpi-php ```
* ``` $ docker build -t tobi312/rpi-php:5.6-fpm ./5.6-fpm/ ``` 
* ``` $ docker run --name php --link some-sql-container:alias -v /home/pi/html:/var/www/html -e PHP_ERRORS=1 -e PHP_UPLOAD_MAX_FILESIZE=250 -d tobi312/rpi-php:5.6-fpm ```   

### Environment Variables
* `TZ` (Default: Europe/Berlin)
* `PHP_ERRORS` (set 1 to enable)
* `PHP_MEM_LIMIT` (Value in MB)
* `PHP_POST_MAX_SIZE` (Value in MB)
* `PHP_UPLOAD_MAX_FILESIZE` (Value in MB)
* `PHP_MAX_FILE_UPLOADS`

### You need httpd?, see here: 
* Apache2
	* [DockerHub](https://hub.docker.com/r/tobi312/rpi-apache2/)
	* [GitHub](https://github.com/Tob1asDocker/rpi-apache2)
* NGINX
	* [DockerHub](https://hub.docker.com/r/tobi312/rpi-nginx/)
	* [GitHub](https://github.com/Tob1asDocker/rpi-nginx)

### This Image on
* [DockerHub](https://hub.docker.com/r/tobi312/rpi-php/)
* [GitHub](https://github.com/Tob1asDocker/rpi-php)