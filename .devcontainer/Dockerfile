FROM ubuntu:22.04
USER root


ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && \
    apt install software-properties-common -y && \
    add-apt-repository ppa:deadsnakes/ppa -y

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    build-essential \
    git \
    python3.11-dev \
    python3-pip \
    openssh-server && \
    apt-get -y clean && \
    rm -rf /var/lib/apt/lists/*

RUN mkdir -p /root/workspace
COPY requirements.txt /root/workspace
WORKDIR /root/workspace

RUN python3 -m pip install --upgrade pip
# &&\    python3 -m pip install --upgrade setuptools
RUN python3 -m pip install --user -r requirements.txt

RUN echo 'PATH="$HOME/.local/bin:$PATH"' >> $HOME/.bashrc && \
    echo 'alias python="python3"' >> ~/.bashrc && \
    . $HOME/.bashrc
