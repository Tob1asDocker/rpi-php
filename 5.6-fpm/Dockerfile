FROM balenalib/rpi-raspbian:jessie

MAINTAINER Tobias Hargesheimer <docker@ison.ws>

ENV LANG C.UTF-8
ENV TZ Europe/Berlin
#ENV TERM xterm # export TERM=xterm because Error opening terminal: unknown.

RUN [ "cross-build-start" ]

RUN apt-get update && apt-get install -y \
	nano \
	zip \
	wget \
	curl \
	imagemagick \
	sqlite sqlite3 \
	#sendmail-bin \
	php5 \
	php5-fpm \
	php5-cli \
	php5-json \
	php5-curl \
	php5-gd \
	php5-imagick \
	php5-sqlite \
	php5-pgsql \
	php5-mysql \
	php5-imap \
	php5-xsl \
	php5-ldap \
	php5-memcache \
	php5-mcrypt \
	#php5-xdebug \
	php5-intl \
	#php5-xmlrpc \
	php-pear \
	#php5-dbg \
	php5-geoip \
	--no-install-recommends && \
	rm -rf /var/lib/apt/lists/* && \
	mkdir -p /var/www/html && chown -R www-data:www-data /var/www
	
RUN sed -i -e 's/error_log = \/var\/log\/php5-fpm.log/error_log = \/proc\/self\/fd\/2/g' /etc/php5/fpm/php-fpm.conf && \
	sed -i -e 's/;daemonize = yes/daemonize = no/g' /etc/php5/fpm/php-fpm.conf && \
	sed -i -e 's/;access.log = log\/$pool.access.log/access.log = \/proc\/self\/fd\/2/g' /etc/php5/fpm/pool.d/www.conf && \
	sed -i -e 's/;catch_workers_output = yes/catch_workers_output = yes/g' /etc/php5/fpm/pool.d/www.conf && \
	sed -i -e 's/;clear_env = no/clear_env = no/g' /etc/php5/fpm/pool.d/www.conf && \
	sed -i -e 's/listen = \/var\/run\/php5-fpm.sock/listen = [::]:9000/g' /etc/php5/fpm/pool.d/www.conf

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

RUN [ "cross-build-end" ]	

VOLUME /var/www/html /etc/php5/fpm/pool.d/ /var/lib/php5/sessions
EXPOSE 9000

ENTRYPOINT ["/entrypoint.sh"]
CMD ["php5-fpm"]
