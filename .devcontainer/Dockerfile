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
    vim \
    curl \
    tree \
    python3.11-dev \
    python3-pip \
    python3-tk \
    ca-certificates \
    openssh-server && \
    apt-get -y clean && \
    rm -rf /var/lib/apt/lists/*

RUN mkdir -p /root/workspace
COPY requirements.txt /root/workspace
WORKDIR /root/workspace

RUN curl -o ~/.git-completion.bash https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash \
        -o ~/.git-prompt.sh https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh

RUN python3 -m pip install --upgrade pip
# &&\    python3 -m pip install --upgrade setuptools
RUN python3 -m pip install --user -r requirements.txt

RUN echo 'PATH="$HOME/.local/bin:$PATH"' >> $HOME/.bashrc && \
    echo 'alias python="python3"' >> ~/.bashrc && \
    . $HOME/.bashrc

RUN echo 'source ~/.git-completion.bash' >> ~/.bashrc
RUN echo 'source ~/.git-prompt.sh\nGIT_PS1_SHOWDIRTYSTATE=true' >> ~/.bashrc
ENV PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]$(__git_ps1 "(%s)")\$ '
RUN echo "PS1='"${PS1}"'" >> ~/.bashrc
