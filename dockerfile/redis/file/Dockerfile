FROM redis:3.2.12


RUN  cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
COPY redis.conf /usr/local/etc/redis/redis.conf
RUN  mkdir /opt/log/ && mkdir /opt/log/redis
RUN  chown -R redis:redis /data
RUN  chown -R redis:redis /opt/log/redis

CMD [ "redis-server", "/usr/local/etc/redis/redis.conf" ]

VOLUME ["/opt"]
EXPOSE 6379


