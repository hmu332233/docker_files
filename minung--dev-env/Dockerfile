FROM ubuntu:16.04
MAINTAINER minung.han <hmu332233@gmail.com>

RUN apt-get update

RUN apt-get install -y git curl

# Install nvm with node and npm
ENV NVM_DIR /usr/local/nvm # or ~/.nvm , depending
ENV NODE_VERSION 8.11.3

RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
RUN . $NVM_DIR/nvm.sh
RUN nvm install $NODE_VERSION

# set locale ko_KR
RUN apt-get install -y locales

ENV LANG ko_KR.UTF-8
ENV LANGUAGE ko_KR.UTF-8

RUN locale-gen ko_KR.UTF-8
RUN update-locale LANG=ko_KR.UTF-8
RUN dpkg-reconfigure locales

RUN git config --global user.name "minung.han" && git config --global user.email "hmu332233@gmail.com"

CMD /bin/bash
