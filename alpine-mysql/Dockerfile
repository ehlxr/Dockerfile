FROM alpine:latest
LABEL maintainer="ehlxr.me@gmail.com"

WORKDIR /app
VOLUME /app

RUN apk add --update --no-cache mysql mysql-client \
    && rm -f /var/cache/apk/*

COPY my.cnf /etc/mysql/my.cnf
COPY startup.sh /startup.sh

EXPOSE 3306
CMD ["/startup.sh"]
