FROM debian:stretch-slim

MAINTAINER Ob Rzwo <obr2pd@gmail.com>

RUN export DEBIAN_FRONTEND=noninteractive
ENV DEBIAN_FRONTEND noninteractive
RUN dpkg-divert --local --rename --add /sbin/initctl

RUN apt-get update
RUN apt-get install -y git gnupg
WORKDIR /opt/
ADD https://deb.nodesource.com/setup_8.x nodesource_setup.sh
RUN chmod +x nodesource_setup.sh
RUN ./nodesource_setup.sh
RUN apt-get install -y nodejs 
RUN /usr/bin/nodejs -v
RUN /usr/bin/npm -v
RUN /usr/bin/npm install -g yarn
RUN git clone --recursive https://github.com/qgis/qwc2-demo-app.git
WORKDIR /opt/qwc2-demo-app/
RUN /usr/bin/yarn install 
EXPOSE 8081
CMD /usr/bin/yarn start

