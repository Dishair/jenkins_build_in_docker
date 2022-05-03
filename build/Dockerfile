FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

# update packages
RUN apt-get update

# Install docker  git maven
RUN apt-get -y install docker.io git maven

VOLUME /war-folder /boxfuse-origin/target