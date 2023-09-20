# Build Ansible image
FROM debian:11.6-slim
LABEL maintainer "Morgan Conlon <morgan.conlon@click-technology.com>"
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

ARG ANSIBLE_LOG_PATH=/var/log/ansible
WORKDIR /ansible

RUN mkdir -p ${ANSIBLE_LOG_PATH} && \
    touch ${ANSIBLE_LOG_PATH}/ansible.log && \
    chmod 666 ${ANSIBLE_LOG_PATH}/ansible.log

RUN apt-get update -qq && \
    DEBIAN_FRONTEND=noninteractive apt-get -y --no-install-recommends install  \
    apt-utils=2.2.4 \
    curl=7.74.0-1.3+deb11u7 \
    git=1:2.30.2-1+deb11u2 \
    python3=3.9.2-3 \
    python3-pip=20.3.4-4+deb11u1 \
    python-is-python3=3.9.2-1 &&\
    apt-get clean &&\
    rm -rf /var/lib/apt/lists/*

COPY requirements.txt requirements.txt
RUN  python3 -m pip install --no-cache-dir -r requirements.txt
