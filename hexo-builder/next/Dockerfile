# docker build -t ehlxr/hexo-builder:next .
FROM node:alpine
LABEL maintainer="ehlxr.me@gmail.com"
WORKDIR /hexo

COPY package.json package.json

RUN apk add --update --no-cache --virtual=build-dependencies git yarn \
    # && npm config set registry https://registry.npm.taobao.org \
    # && npm install \
    && yarn config set registry https://registry.npm.taobao.org/ \
    && yarn \
    && ln -s /hexo/node_modules/hexo-cli/bin/hexo /usr/local/bin/hexo \
    && ln -s /hexo/node_modules/gulp/bin/gulp.js /usr/local/bin/gulp \
    && apk del build-dependencies \
    && rm -rf /var/cache/apk/* \
    && rm -rf /tmp/* \
    && rm package*.json \
    # && npm cache clean --force
    && yarn cache clean