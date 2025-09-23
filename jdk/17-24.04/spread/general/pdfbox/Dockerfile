ARG ROCK
FROM ubuntu:24.04 as builder
ARG CHISEL_VERSION=1.2.0
ARG TARGETARCH=amd64

RUN apt-get update && \
     apt-get install -y maven

     SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]
ADD https://github.com/canonical/chisel/releases/download/v${CHISEL_VERSION}/chisel_v${CHISEL_VERSION}_linux_${TARGETARCH}.tar.gz chisel.tar.gz
RUN tar -xvf chisel.tar.gz -C /usr/bin/
RUN mkdir -p /rootfs \
        && chisel cut --root /rootfs base-files_base coreutils_bins dash_bins

FROM $ROCK

COPY --from=builder /rootfs /
COPY --from=builder /etc/maven /etc/maven
COPY --from=builder /usr/share/java /usr/share/java
COPY --from=builder /usr/share/maven /usr/share/maven
