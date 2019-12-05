FROM alpine
# ehlxr/alpine
LABEL maintainer="ehlxr <ehlxr.me@gmail.com>"

ENV TZ "Asia/Shanghai"

# RUN apk upgrade --update \
#     && apk add tzdata \
#     && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
#     && echo ${TZ} > /etc/timezone \
#     && rm -rf /var/cache/apk/*

COPY Shanghai /usr/share/zoneinfo/${TZ}
RUN ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone