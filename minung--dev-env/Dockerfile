FROM ubuntu:14.04
MAINTAINER minung.han <hmu332233@gmail.com>

RUN apt-get update

RUN apt-get install -y git

# set locale ko_KR
RUN apt-get install -y locales

ENV LANG ko_KR.UTF-8
ENV LANGUAGE ko_KR.UTF-8

RUN locale-gen ko_KR.UTF-8
RUN update-locale LANG=ko_KR.UTF-8
RUN dpkg-reconfigure locales

RUN git config --global user.name "minung.han" && git config --global user.email "hmu332233@gmail.com"

CMD /bin/bash
