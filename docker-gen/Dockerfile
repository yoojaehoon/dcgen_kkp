FROM ubuntu:14.04

MAINTAINER jaebung <jaebung2@gmail.com>

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get clean

ADD docker-gen /usr/bin/docker-gen
ENV DOCKER_HOST unix:///docker.sock

VOLUME ["/etc/docker-gen/", "/etc/nginx/sites-enabled/"]
WORKDIR /etc/docker-gen/

CMD ["/usr/bin/docker-gen", "-watch", "-only-exposed", "-notify-sighup=nginx", "nginx.tmpl", "/etc/nginx/sites-enabled/nginx-reverse-proxy"]
