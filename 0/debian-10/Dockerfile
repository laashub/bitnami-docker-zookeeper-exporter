FROM bitnami/minideb:buster
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ca-certificates curl libc6 procps sudo unzip wget
RUN wget -nc -P /tmp/bitnami/pkg/cache/ https://downloads.bitnami.com/files/stacksmith/zookeeper-exporter-0.1.3-0-linux-amd64-debian-10.tar.gz && \
    echo "e62ed969c11b3d8d5dcac16974def80862b255cbf9cebfbd7bd55f6900cfd217  /tmp/bitnami/pkg/cache/zookeeper-exporter-0.1.3-0-linux-amd64-debian-10.tar.gz" | sha256sum -c - && \
    tar -zxf /tmp/bitnami/pkg/cache/zookeeper-exporter-0.1.3-0-linux-amd64-debian-10.tar.gz -P --transform 's|^[^/]*/files|/opt/bitnami|' --wildcards '*/files' && \
    rm -rf /tmp/bitnami/pkg/cache/zookeeper-exporter-0.1.3-0-linux-amd64-debian-10.tar.gz
RUN apt-get update && apt-get upgrade && \
    rm -r /var/lib/apt/lists /var/cache/apt/archives
RUN ln -sf /opt/bitnami/zookeeper-exporter/bin/zookeeper-exporter /usr/local/bin/zookeeper-exporter

ENV BITNAMI_APP_NAME="zookeeper-exporter" \
    BITNAMI_IMAGE_VERSION="0.1.3-debian-10-r14" \
    PATH="/opt/bitnami/zookeeper-exporter/bin:$PATH"

EXPOSE 8080

WORKDIR /opt/bitnami/zookeeper-exporter
USER 1001
ENTRYPOINT [ "zookeeper-exporter" ]
