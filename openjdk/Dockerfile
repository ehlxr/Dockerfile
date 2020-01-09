FROM adoptopenjdk/openjdk8:alpine
# ehlxr/openjdk8:alpine
LABEL maintainer="ehlxr <ehlxr.me@gmail.com>"

ENV TZ "Asia/Shanghai"

COPY Shanghai /usr/share/zoneinfo/${TZ}
RUN ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone