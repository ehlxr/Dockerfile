# https://github.com/etcd-io/etcd/blob/master/Documentation/op-guide/container.md#docker
FROM alpine:latest

ARG ETCD_VER=v3.0.14
ARG ETCD_DOWNLOAD_URL=https://github.com/coreos/etcd/releases/download

ENV DATA_DIR=/var/lib/etcd/
ENV IP=0.0.0.0
ENV NODE_NAME=node1
ENV CLUSTER=${NODE_NAME}=http://${IP}:2380
ENV TOKEN=my-etcd-token
ENV CLUSTER_STATE=new

VOLUME [ "${DATA_DIR}" ]

RUN wget ${ETCD_DOWNLOAD_URL}/${ETCD_VER}/etcd-${ETCD_VER}-linux-amd64.tar.gz \
    && tar -xzvf etcd*.tar.gz \
    && mv etcd*/etcd /usr/local/bin/ \
    # && mv etcd*/etcdctl /usr/local/bin/ \
    && rm -rf etcd* \
    && mkdir -p ${DATA_DIR} \
    # Alpine Linux doesn't use pam, which means that there is no /etc/nsswitch.conf,
    # but Golang relies on /etc/nsswitch.conf to check the order of DNS resolving
    # (see https://github.com/golang/go/commit/9dee7771f561cf6aee081c0af6658cc81fac3918)
    # To fix this we just create /etc/nsswitch.conf and add the following line:
    && echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf

EXPOSE 2379 2380

CMD ["sh", "-c", "etcd --data-dir ${DATA_DIR} --name ${NODE_NAME} \
    --initial-advertise-peer-urls http://${IP}:2380 --listen-peer-urls http://${IP}:2380 \
    --advertise-client-urls http://${IP}:2379 --listen-client-urls http://${IP}:2379 \
    --initial-cluster ${CLUSTER} \
    --initial-cluster-state ${CLUSTER_STATE} --initial-cluster-token ${TOKEN}"]