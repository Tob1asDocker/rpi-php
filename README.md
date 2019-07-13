# PHP on Raspberry Pi / armhf

### Supported tags and respective `Dockerfile` links
-	[`7.0-fpm`, `latest` (*Dockerfile*)](https://github.com/TobiasH87Docker/rpi-php/blob/master/7.0-fpm/Dockerfile)
-	[`5.6-fpm` (*Dockerfile*)](https://github.com/TobiasH87Docker/rpi-php/blob/master/5.6-fpm/Dockerfile)

### Note:
Alternatively I recommend to use the official [ARM-Images](https://github.com/docker-library/official-images#architectures-other-than-amd64), which are now available:  
[arm32v5](https://hub.docker.com/r/arm32v5/php/), [arm32v6](https://hub.docker.com/r/arm32v6/php/), [arm32v7](https://hub.docker.com/r/arm32v7/php/), [arm64v8](https://hub.docker.com/r/arm64v8/php/)

### What is PHP?

PHP is a server-side scripting language designed for web development, but which can also be used as a general-purpose programming language. PHP can be added to straight HTML or it can be used with a variety of templating engines and web frameworks. PHP code is usually processed by an interpreter, which is either implemented as a native module on the web-server or as a common gateway interface (CGI).
> [wikipedia.org/wiki/PHP](https://en.wikipedia.org/wiki/PHP) and [php.net](https://php.net)

![logo](https://raw.githubusercontent.com/docker-library/docs/master/php/logo.png)

### How to use this image
* ``` $ docker pull tobi312/rpi-php:5.6-fpm ```
* Optional: ``` $ mkdir -p /home/pi/html ```
* ``` $ docker run --name php --link some-sql-container:alias -v /home/pi/html:/var/www/html -e PHP_ERRORS=1 -e PHP_UPLOAD_MAX_FILESIZE=250 -d tobi312/rpi-php:5.6-fpm ``` 

or build it yourself
* ``` $ git clone https://github.com/TobiasH87Docker/rpi-php.git && cd rpi-php ```
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
	* [GitHub](https://github.com/TobiasH87Docker/rpi-apache2)
* NGINX
	* [DockerHub](https://hub.docker.com/r/tobi312/rpi-nginx/)
	* [GitHub](https://github.com/TobiasH87Docker/rpi-nginx)

### This Image on
* [DockerHub](https://hub.docker.com/r/tobi312/rpi-php/)
* [GitHub](https://github.com/TobiasH87Docker/rpi-php)