FROM ubuntu:16.04
MAINTAINER minung.han <hmu332233@gmail.com>

# Replace shell with bash so we can source files
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# Set debconf to run non-interactively
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

# Install base dependencies
RUN apt-get update && apt-get install -y -q --no-install-recommends \
        apt-transport-https \
        build-essential \
        ca-certificates \
        curl \
        git \
        libssl-dev \
        wget
    # && rm -rf /var/lib/apt/lists/*

# ENV NVM_DIR /usr/local/nvm # or  , depending
# ENV NODE_VERSION 8.11.3

# Install nvm with node and npm
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | sh
RUN . ~/.nvm/nvm.sh \
    && nvm install 8.11.3 \
    && nvm alias default 8.11.3 \
    && nvm use default

ENV NODE_PATH ~/.nvm/v8.11.3/lib/node_modules
ENV PATH      ~/.nvm/v8.11.3/bin:$PATH

# set locale ko_KR
RUN apt-get install -y locales language-pack-ko

ENV LANG ko_KR.UTF-8
ENV LANGUAGE ko_KR.UTF-8

RUN locale-gen ko_KR.UTF-8
RUN update-locale LANG=ko_KR.UTF-8
RUN dpkg-reconfigure locales

RUN git config --global user.name "minung.han" && git config --global user.email "hmu332233@gmail.com"

CMD /bin/bash
