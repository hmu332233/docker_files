FROM resinci/npm-x86_64-ubuntu-node8:latest
MAINTAINER minung.han <hmu332233@gmail.com>

RUN add-apt-repository ppa:git-core/ppa
RUN apt-get update && \
    apt-get install -y git curl locales

# set locale ko_KR
ENV LANG ko_KR.UTF-8
ENV LANGUAGE ko_KR.UTF-8

RUN locale-gen ko_KR.UTF-8  && \
    update-locale LANG=ko_KR.UTF-8 && \
    dpkg-reconfigure locales

# git config
RUN git config --global user.name "minung.han" && git config --global user.email "hmu332233@gmail.com"


# remove apt-get list
RUN rm -rf /var/lib/apt/lists/*

CMD /bin/bash
