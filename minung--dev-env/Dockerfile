FROM ubuntu:16.04
MAINTAINER minung.han <hmu332233@gmail.com>

# replace shell with bash so we can source files
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# set debconf to run non-interactively
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

# install base dependencies
RUN apt-get update && apt-get install -y -q --no-install-recommends \
        apt-transport-https \
        build-essential \
        ca-certificates \
        curl \
        git \
        libssl-dev \
        wget

# install nodejs
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash
RUN apt-get install -y nodejs

# set locale ko_KR
RUN apt-get install -y locales language-pack-ko

ENV LANG ko_KR.UTF-8
ENV LANGUAGE ko_KR.UTF-8

RUN locale-gen ko_KR.UTF-8
RUN update-locale LANG=ko_KR.UTF-8
RUN dpkg-reconfigure locales

RUN git config --global user.name "minung.han" && git config --global user.email "hmu332233@gmail.com"

# remove apt-get update list
RUN rm -rf /var/lib/apt/lists/*

CMD /bin/bash
