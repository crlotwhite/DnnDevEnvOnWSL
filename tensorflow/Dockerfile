FROM tensorflow/tensorflow:latest-gpu 

ARG USER
ARG PASSWD

RUN /bin/bash -c 'useradd -m -s /bin/bash -g root ${USER}; echo "${USER}:${PASSWD}*" | chpasswd'

COPY ./wsl.conf /etc/wsl.conf
RUN /bin/bash -c 'echo "default=${USER}" >> /etc/wsl.conf; \
    echo "${USER} ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers;'