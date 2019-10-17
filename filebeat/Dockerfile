FROM ehlxr/alpine

LABEL maintainer="ehlxr <ehlxr.me@gmail.com>"

ENV FILEBEAT_VERSION=6.5.4

# COPY filebeat.yml /filebeat.yml

RUN apk add libc6-compat \
    && wget https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz \
    && tar xzvf filebeat-*.tar.gz \
    && mv filebeat-*/filebeat /usr/local/bin/ \
    && rm -rf filebeat-* \
    && rm -rf /var/cache/apk/*

# CMD ["filebeat", "-c", "filebeat.yml"]