FROM openjdk:8-jre

# 新建目录
RUN mkdir /opt/jar/
# 把jar包复制进去
# 需要改为你运行的jar包名称
ADD admin-0.0.1-SNAPSHOT.jar /opt/jar/

#时区 
RUN echo "Asia/Shanghai" > /etc/timezone

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

EXPOSE 8080

WORKDIR /opt/

CMD ["java", "-jar","-Dfile.encoding=UTF-8","/opt/jar/admin-0.0.1-SNAPSHOT.jar"]
