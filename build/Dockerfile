FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

# update packages
RUN apt-get update




# Install git maven docker
RUN apt-get -y install git maven docker.io su




# CMD ["/usr/bin/dockerd",">","/dev/null","2>&1","&"]

# Create volume with app
# RUN mkdir -p /var/lib/jenkins/workspace/jenkins_build_in_docker/target
# VOLUME /var/lib/jenkins/workspace/jenkins_build_in_docker/target