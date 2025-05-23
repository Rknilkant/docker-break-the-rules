FROM ubuntu:22.04

# Avoids tzdata prompt
ENV DEBIAN_FRONTEND=noninteractive

# Install XFCE and VNC server
RUN apt update && apt install -y \
    xfce4 \
    tightvncserver \
    dbus-x11 \
    x11-xserver-utils \
    sudo \
    nano \
    wget \
    net-tools

# Create user and set password
RUN useradd -m docker && \
    echo "docker:docker" | chpasswd && \
    adduser docker sudo

USER docker
WORKDIR /home/docker

ENV USER=docker

# Configure VNC password
RUN mkdir -p /home/docker/.vnc && \
    echo "docker" | vncpasswd -f > /home/docker/.vnc/passwd && \
    chmod 600 /home/docker/.vnc/passwd

# Create minimal xstartup script
RUN echo "#!/bin/bash\nstartxfce4 &" > /home/docker/.vnc/xstartup && \
    chmod +x /home/docker/.vnc/xstartup

# Set default command to launch VNC server on display :1
# CMD ["vncserver", ":1", "-geometry", "1280x800", "-depth", "24"]
CMD vncserver :1 -geometry 1280x800 -depth 24 && tail -F /home/docker/.vnc/*.log
