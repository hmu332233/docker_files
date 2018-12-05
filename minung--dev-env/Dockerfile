FROM resinci/npm-x86_64-ubuntu-node8:latest
MAINTAINER minung.han <hmu332233@gmail.com>

RUN add-apt-repository ppa:git-core/ppa
RUN apt-get update && \
    apt-get install -y git vim curl locales language-pack-ko

RUN wget --no-check-certificate -q  https://raw.githubusercontent.com/petervanderdoes/gitflow-avh/develop/contrib/gitflow-installer.sh && bash gitflow-installer.sh install stable; rm gitflow-installer.sh

# install npm package
RUN npm install -g @hmu332233/minung--dev-tools

# set locale ko_KR
ENV LANG ko_KR.UTF-8
ENV LANGUAGE ko_KR.UTF-8

RUN locale-gen ko_KR.UTF-8  && \
    update-locale LANG=ko_KR.UTF-8 && \
    dpkg-reconfigure locales

RUN bash -c 'echo "Asia/Seoul" > /etc/timezone' && \
    dpkg-reconfigure -f noninteractive tzdata

# git config
RUN git config --global user.name "minung.han" && git config --global user.email "hmu332233@gmail.com"


# remove apt-get list
RUN rm -rf /var/lib/apt/lists/*

CMD /bin/bash
