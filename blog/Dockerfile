FROM ehlxr/hexo:latest
# WORKDIR /hexo
COPY . .

RUN hexo generate && gulp

# ENTRYPOINT [ "hexo", "server" ]
# CMD [ "-p", "80" ]

FROM nginx:alpine
LABEL maintainer="ehlxr.me@gmail.com"
WORKDIR /usr/share/nginx/html
COPY --from=0 /hexo/public .
ENTRYPOINT ["nginx", "-g", "daemon off;"]