FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

# update packages
RUN apt-get update




# Install git maven
RUN apt-get -y install git maven docker


# Install docker
# RUN apt-get update && \
#    apt-get -qy full-upgrade && \
#    apt-get install -qy curl && \
#    apt-get install -qy curl && \
#    curl -sSL https://get.docker.com/ | sh


CMD ["dockerd",">","/dev/null","2>&1","&"]

# Create volume with app
# RUN mkdir -p /var/lib/jenkins/workspace/jenkins_build_in_docker/target
# VOLUME /var/lib/jenkins/workspace/jenkins_build_in_docker/target