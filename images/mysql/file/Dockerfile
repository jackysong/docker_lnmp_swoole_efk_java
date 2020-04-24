FROM mysql:5.6

ADD mysqld.cnf /etc/mysql/mysql.conf.d
RUN cp  /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN usermod -u 1000 mysql && chown mysql.mysql /var/run/mysqld/
EXPOSE 3306
