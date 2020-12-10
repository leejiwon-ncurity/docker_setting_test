# ubuntu-openjdk-8-jdk
#
# VERSION               0.0.3
#
# Extends ubuntu-base with java 8 openjdk jdk installation
#
FROM ubuntu:bionic

# This is in accordance to : https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04
RUN apt-get update && \
	apt-get install -y openjdk-11-jdk && \
	apt-get install -y ant && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/* && \
	rm -rf /var/cache/oracle-jdk11-installer;
	
# Fix certificate issues, found as of 
# https://bugs.launchpad.net/ubuntu/+source/ca-certificates-java/+bug/983302
RUN apt-get update && \
	apt-get install -y ca-certificates-java && \
	apt-get clean && \
	update-ca-certificates -f && \
	rm -rf /var/lib/apt/lists/* && \
	rm -rf /var/cache/oracle-jdk11-installer;

# git install
RUN apt update && \
	apt install -y git;

#PostgreSQL install
RUN apt-get update && \
	apt-get install -y postgresql-10 postgresql-contrib;

# Setup JAVA_HOME, this is useful for docker commandline
RUN export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64 && \
	export PATH=$PATH:/usr/lib/jvm/java-11-openjdk-amd64/bin

EXPOSE 10000 9900