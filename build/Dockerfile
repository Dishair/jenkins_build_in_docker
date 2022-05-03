FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

# update packages
RUN apt-get update




# Install git maven docker
RUN apt-get -y install git maven docker.io sudo

RUN groupadd docker
RUN usermod -aG docker $USER
RUN newgrp docker 
RUN useradd -u 8877 user
USER user

# CMD ["/usr/bin/dockerd",">","/dev/null","2>&1","&"]

# Create volume with app
# RUN mkdir -p /var/lib/jenkins/workspace/jenkins_build_in_docker/target
# VOLUME /var/lib/jenkins/workspace/jenkins_build_in_docker/target