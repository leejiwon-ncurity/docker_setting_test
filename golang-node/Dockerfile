# ubuntu-openjdk-8-jdk
#
# VERSION               0.0.3
#
# Extends ubuntu-base with java 8 openjdk jdk installation
#
FROM ubuntu:bionic

# This is in accordance to : https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04
RUN apt-get update && \
	apt-get -y upgrade && \
	apt update && \
	apt -y upgrade && \ 
	apt install -y curl && \
	apt install -y wget;
	
# golang install
RUN wget https://dl.google.com/go/go1.15.6.linux-amd64.tar.gz && \
	mkdir -p /usr/local/bin && \
	mkdir -p /usr/local/pkg && \
	mkdir -p /usr/local/src && \
	tar -C /usr/local -xzf go1.15.6.linux-amd64.tar.gz && \
	export GOROOT=/usr/local/go && \
	export PATH=$PATH:$GOROOT/bin && \
	rm -rf go1.15.6.linux-amd64.tar.gz && \
	go version;


# nodejs install
RUN curl -sL https://deb.nodesource.com/setup_14.x -o nodesource_setup.sh && \
	bash nodesource_setup.sh;

RUN	apt-get update && \
	apt-get -y upgrade && \
	apt-get -y install nodejs && \
	apt-get -y install build-essential;


# git install
RUN apt update && \
	apt install -y git;