FROM node:12
MAINTAINER minung.han <hmu332233@gmail.com>

# set locale ko_KR
RUN ln -snf /usr/share/zoneinfo/Asia/Seoul /etc/localtime
ENV DEBIAN_FRONTEND noninteractive
ENV LC_ALL C.UTF-8

RUN apt-get update && \
    apt-get install -y libghc-zlib-dev libcurl4-gnutls-dev gettext 

RUN wget --no-check-certificate -q  https://raw.githubusercontent.com/petervanderdoes/gitflow-avh/develop/contrib/gitflow-installer.sh && bash gitflow-installer.sh install stable; rm gitflow-installer.sh

RUN wget https://github.com/git/git/archive/v2.24.0.zip -O latestgit.zip; unzip latestgit.zip; cd git-2.24.0; make prefix=/usr/local all; make prefix=/usr/local install; cd ..; rm -rf git-2.24.0 latestgit.zip

RUN dpkg-reconfigure --frontend noninteractive tzdata

# install npm package
RUN npm install -g @hmu332233/minung--dev-tools yarn
RUN chmod u+x /usr/local/bin/yarn

# git config
RUN git config --global user.name "minung.han" && git config --global user.email "hmu332233@gmail.com" &&  git config --global core.eol lf

# remove apt-get list
RUN rm -rf /var/lib/apt/lists/*

CMD /bin/bash
