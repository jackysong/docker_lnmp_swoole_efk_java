FROM golang:1.12

ADD sources.list    /etc/apt/sources.list
# ADD supervisord.conf    /etc/supervisor/conf.d/sd.conf

ENV GOPATH "/gowork"
ENV GOPROXY "https://mirrors.aliyun.com/goproxy/"
ENV GO111MODULE on


# 安装modules
RUN apt-get update && apt-get install -y \
	          supervisor \
						libfreexl-dev \
            && apt-get clean 



# CMD ["supervisord"]
