FROM registry.cn-hangzhou.aliyuncs.com/kai12/php:7.1.9

ADD php.ini    /usr/local/etc/php/php.ini
ADD php-fpm.d/www.conf    /usr/local/etc/php-fpm.d/www.conf

RUN docker-php-ext-install bcmath

#xdebug
ADD xdebug-2.6.1.tgz /opt/

RUN cd /opt/xdebug-2.6.1 \
&& phpize \
&& ./configure \
&& make \
&& make install \
&& make test \
&& echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
&& echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/conf.d/xdebug.ini \
&& echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
&& echo "xdebug.remote_handler=dbgp" >> /usr/local/etc/php/conf.d/xdebug.ini \
&& echo "xdebug.remote_host=docker.for.mac.host.internal" >> /usr/local/etc/php/conf.d/xdebug.ini \ 
&& echo "xdebug.remote_port=9001" >> /usr/local/etc/php/conf.d/xdebug.ini \
&& echo "xdebug.remote_autostart=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
&& echo "xdebug.remote_connect_back=0" >> /usr/local/etc/php/conf.d/xdebug.ini \
&& echo "xdebug.remote_log=/opt/log/php/xdebug_remote.log" >> /usr/local/etc/php/conf.d/xdebug.ini \
&& rm -r /opt/xdebug-2.6.1

