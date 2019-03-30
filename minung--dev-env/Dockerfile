FROM resinci/npm-x86_64-ubuntu-node8:latest
MAINTAINER minung.han <hmu332233@gmail.com>

RUN add-apt-repository ppa:git-core/ppa
RUN apt-get update && \
    apt-get install -y git vim curl

RUN wget --no-check-certificate -q  https://raw.githubusercontent.com/petervanderdoes/gitflow-avh/develop/contrib/gitflow-installer.sh && bash gitflow-installer.sh install stable; rm gitflow-installer.sh

# install npm package
RUN npm install -g @hmu332233/minung--dev-tools yarn

# set locale ko_KR
RUN ln -snf /usr/share/zoneinfo/Asia/Seoul /etc/localtime && \
    echo Asia/Seoul > /etc/timezone

# git config
RUN git config --global user.name "minung.han" && git config --global user.email "hmu332233@gmail.com"

# remove apt-get list
RUN rm -rf /var/lib/apt/lists/*

CMD /bin/bash
