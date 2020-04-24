FROM node:10.13.0

ADD sources.list    /etc/apt/sources.list
ENV WORK_HOME /home/node
WORKDIR /home/node

RUN mkdir -p ${WORK_HOME}
RUN mkdir -p /opt/log/supervisor
COPY . ${WORK_HOME}

RUN apt-get update && apt-get install -y \
    supervisor \
    && apt-get clean


RUN npm install -g cnpm --registry=https://registry.npm.taobao.org
RUN cnpm install -g gulp && cnpm install -g yarn && yarn config set registry https://registry.npm.taobao.org && npm cache verify


RUN cp -rf ${WORK_HOME}/supervisord.conf /etc/supervisor/conf.d/sd.conf


CMD ["supervisord"]