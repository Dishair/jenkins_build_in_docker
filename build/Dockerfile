FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

# update packages
RUN apt-get update




# Install git maven docker
RUN apt-get -y install git maven docker.io curl

WORKDIR /

# RUN curl -fsSL https://get.docker.com/rootless
# RUN DOCKERD_ROOTLESS_ROOTLESSKIT_FLAGS="-p 0.0.0.0:2376:2376/tcp" \
#  dockerd-rootless.sh \
#  -H tcp://0.0.0.0:2376 \
#  --tlsverify --tlscacert=ca.pem --tlscert=cert.pem --tlskey=key.pem


# CMD ["/usr/bin/dockerd",">","/dev/null","2>&1","&"]

# Create volume with app
# RUN mkdir -p /var/lib/jenkins/workspace/jenkins_build_in_docker/target
# VOLUME /var/lib/jenkins/workspace/jenkins_build_in_docker/target