FROM alpine:latest
LABEL maintainer="ehlxr.me@gmail.com"

ENV TZ "Asia/Shanghai"

WORKDIR /app
VOLUME /data

RUN apk add --update --no-cache mysql mysql-client tzdata \
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && rm -rf /var/cache/apk/*

COPY my.cnf /etc/mysql/my.cnf
COPY startup.sh /startup.sh

EXPOSE 3306
CMD ["/startup.sh"]