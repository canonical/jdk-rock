FROM jdk:latest
USER root
RUN apt-get update && \
        DEBIAN_FRONTEND=noninteractive apt-get install -y \
        maven \
        gdb \
        gradle \
        junit4
USER 584792
