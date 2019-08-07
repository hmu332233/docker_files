FROM resinci/npm-x86_64-ubuntu-node8:latest
MAINTAINER minung.han <hmu332233@gmail.com>

RUN apt-get update && \
    apt-get install -y git vim curl tzdata

RUN wget --no-check-certificate -q  https://raw.githubusercontent.com/petervanderdoes/gitflow-avh/develop/contrib/gitflow-installer.sh && bash gitflow-installer.sh install stable; rm gitflow-installer.sh

# install npm package
RUN npm install -g @hmu332233/minung--dev-tools yarn
RUN chmod u+x /usr/local/bin/yarn

# set locale ko_KR
RUN bash -c 'echo "Asia/Seoul" > /etc/timezone' && dpkg-reconfigure -f noninteractive tzdata
ENV LC_ALL C.UTF-8

# git config
RUN git config --global user.name "minung.han" && git config --global user.email "hmu332233@gmail.com" &&  git config --global core.eol lf

# remove apt-get list
RUN rm -rf /var/lib/apt/lists/*

CMD /bin/bash
