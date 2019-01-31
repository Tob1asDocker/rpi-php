FROM balenalib/rpi-raspbian:stretch

MAINTAINER Tobias Hargesheimer <docker@ison.ws>

ENV LANG C.UTF-8
ENV TZ Europe/Berlin
#ENV TERM xterm # export TERM=xterm because Error opening terminal: unknown.

RUN [ "cross-build-start" ]

RUN apt-get update && apt-get install -y \
	nano \
	zip unzip \
	wget \
	curl \
	imagemagick \
	sqlite sqlite3 \
	#sendmail-bin \
	php7.0 \
	php7.0-fpm \
	php7.0-cli \
	php7.0-json \
	php7.0-curl \
	php7.0-gd \
	php-imagick \
	php7.0-sqlite3 \
	php7.0-pgsql \
	php7.0-mysql \
	php7.0-imap \
	php7.0-xsl \
	php7.0-ldap \
	php-memcache \
	php7.0-mcrypt \
	#php-xdebug \
	php7.0-intl \
	#php7.0-xmlrpc \
	php7.0-xml \
	php-pear \
	php-geoip \
	php7.0-opcache \
	php-gettext \
	php7.0-zip \
	--no-install-recommends && \
	rm -rf /var/lib/apt/lists/* && \
	mkdir -p /var/www/html && chown -R www-data:www-data /var/www
	
RUN sed -i -e 's/error_log = \/var\/log\/php7.0-fpm.log/error_log = \/proc\/self\/fd\/2/g' /etc/php/7.0/fpm/php-fpm.conf && \
	sed -i -e 's/;daemonize = yes/daemonize = no/g' /etc/php/7.0/fpm/php-fpm.conf && \
	sed -i -e 's/;access.log = log\/$pool.access.log/access.log = \/proc\/self\/fd\/2/g' /etc/php/7.0/fpm/pool.d/www.conf && \
	sed -i -e 's/;catch_workers_output = yes/catch_workers_output = yes/g' /etc/php/7.0/fpm/pool.d/www.conf && \
	sed -i -e 's/;clear_env = no/clear_env = no/g' /etc/php/7.0/fpm/pool.d/www.conf && \
	sed -i -e 's/listen = \/run\/php\/php7.0-fpm.sock/listen = [::]:9000/g' /etc/php/7.0/fpm/pool.d/www.conf && \
	mkdir -p /run/php

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

RUN [ "cross-build-end" ]	

VOLUME /var/www/html /etc/php/7.0/fpm/pool.d/ /var/lib/php/sessions
EXPOSE 9000

ENTRYPOINT ["/entrypoint.sh"]
CMD ["php-fpm7.0"]
