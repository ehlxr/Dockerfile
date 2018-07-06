FROM ehlxr/hexo:latest
# WORKDIR /hexo
COPY . .

RUN hexo generate && gulp

# ENTRYPOINT [ "hexo", "server" ]
# CMD [ "-p", "80" ]

FROM nginx:alpine
LABEL maintainer="ehlxr.me@gmail.com"
ENV TZ "Asia/Shanghai"
WORKDIR /usr/share/nginx/html
COPY --from=0 /hexo/public .
RUN apk upgrade --update \
    && apk add tzdata \
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && rm -rf /var/cache/apk/*
ENTRYPOINT ["nginx", "-g", "daemon off;"]