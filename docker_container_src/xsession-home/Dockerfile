FROM ubuntu:20.04

ARG user_uid
ARG user_gid
ARG user_name
ARG group_name


# python
RUN apt-get update && apt-get install -y \
    python3.8 \
    python3-pip \
    python3.8-venv \
    sudo \
    pep8 \
    git \
    vim

# needed for graphviz installation
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get install -y \
    graphviz \
    graphviz-dev \
    libgraphviz-dev

RUN python3.8 -m pip install pip

# For click python package
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

RUN export uid=$user_uid gid=$user_gid && \
    mkdir -p /home/$user_name && \
    mkdir -p /etc/sudoers.d && \
    echo $user_name":x:${uid}:${gid}:Container builder,,,:/home/"$user_name":/bin/bash" >> /etc/passwd && \
    echo $user_name":x:${uid}:" >> /etc/group && \
    echo $user_name" ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$user_name && \
    chmod 0440 /etc/sudoers.d/$user_name

# Mera proxy
ENV http_proxy="http://proxy.merann.com:8080"
ENV https_proxy="http://proxy.merann.com:8080"
ENV ftp_proxy="http://proxy.merann.com:8080"

# Credentials for S3 should be set up in ~/.aws/config file as "mera" profile

USER $user_name:$group_name
ENV HOME=/home/$user_name

WORKDIR /home/$user_name

