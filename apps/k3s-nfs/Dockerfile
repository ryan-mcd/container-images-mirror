FROM docker.io/rancher/k3s:v1.25.6-k3s1
LABEL "org.opencontainers.image.source"="https://github.com/ryan-mcd/container-images-mirror"

RUN set -ex; \
    apk add --no-cache iptables ip6tables nfs-utils;

ENTRYPOINT ["/opt/k3s/bin/k3s"]
CMD ["agent"]
