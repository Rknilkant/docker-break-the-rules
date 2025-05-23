FROM ubuntu:22.04

ENV container docker

# Avoid tzdata prompt
ENV DEBIAN_FRONTEND=noninteractive

# Install systemd and useful tools
RUN apt update && apt install -y \
    systemd \
    systemd-sysv \
    dbus \
    sudo \
    iproute2 \
    net-tools \
    vim \
    curl

# Set up a default user (optional)
RUN useradd -m docker && echo "docker:docker" | chpasswd && adduser docker sudo

STOPSIGNAL SIGRTMIN+3

CMD ["/sbin/init"]
