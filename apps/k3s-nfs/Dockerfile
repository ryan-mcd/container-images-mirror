FROM docker.io/rancher/k3s:v1.25.10-k3s1
FROM alpine:latest AS base
LABEL "org.opencontainers.image.source"="https://github.com/ryan-mcd/container-images-mirror"

RUN set -ex; \
    apk add --no-cache iptables ip6tables nfs-utils; \
    echo 'hosts: files dns' > /etc/nsswitch.conf

COPY --from=docker.io/rancher/k3s:v1.25.10-k3s1 /bin /opt/k3s/bin

VOLUME /var/lib/kubelet
VOLUME /var/lib/rancher/k3s
VOLUME /var/lib/cni
VOLUME /var/log

ENV PATH="$PATH:/bin/aux:/opt/k3s/bin:/opt/k3s/bin/aux"
ENV CRI_CONFIG_FILE="/var/lib/rancher/k3s/agent/etc/crictl.yaml"

ENTRYPOINT ["/opt/k3s/bin/k3s"]
CMD ["agent"]