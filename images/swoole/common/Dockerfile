FROM php:7.1-cli
ENV WORK_HOME /home/swoole

RUN mkdir -p ${WORK_HOME}
ADD /package/sources.list    /etc/apt/sources.list
# ADD supervisord.conf    /etc/supervisor/conf.d/sd.conf
ADD build.sh ${WORK_HOME}

RUN apt-get update && apt-get install -y \
	zip \
	bzip2 \
	libssl-dev \
	&& docker-php-ext-install opcache \
	&& docker-php-ext-install sockets \
	&& docker-php-ext-install mysqli \
	&& docker-php-ext-install pdo_mysql \
	&& apt-get clean

ADD /package/swoole-src-1.10.5.tar.gz  ${WORK_HOME}
ADD /package/phpredis-3.0.0.tar.gz  ${WORK_HOME}
ADD /package/hiredis-0.13.3.tar.gz  ${WORK_HOME}
ADD /package/inotify-2.0.0.tgz  ${WORK_HOME}
# COPY my_cron /etc/cron.d/my_cron
# RUN crontab /etc/cron.d/my_cron
# RUN chmod 0644 /etc/cron.d/my_cron

RUN cd ${WORK_HOME} \
	&& cd phpredis-3.0.0 \
	&& phpize \
	&& ./configure \
	&& make \
	&& make install

RUN cd ${WORK_HOME} \
	&& cd inotify-2.0.0 \
	&& phpize \
	&& ./configure \
	&& make \
	&& make install


RUN cd ${WORK_HOME} \
	&& cd hiredis-0.13.3 \
	&& make -j install \
	&& ldconfig


RUN cd ${WORK_HOME} \
	&& cd swoole-src-1.10.5 \
	&& phpize \
	&& ./configure --enable-async-redis --enable-openssl \
	&& make \
	&& make install

RUN cd ${WORK_HOME} \
	&& cd phpredis-3.0.0 \
	&& phpize \
	&& ./configure \
	&& make \
	&& make install

RUN docker-php-ext-enable redis && docker-php-ext-enable swoole && docker-php-ext-enable inotify


WORKDIR /opt


VOLUME ["/opt"]

# CMD ["sh","/home/swoole/build.sh"]
CMD ["php","/opt/web/k12_swoole/start_swoole_server.php","start","-D"]




