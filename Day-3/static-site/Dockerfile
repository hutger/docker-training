FROM ubuntu
MAINTAINER nutanix@gmail.com 

RUN apt-get -y update && apt-get -y upgrade 
RUN apt-get install -y git vim nginx

EXPOSE 80

VOLUME /usr/share/nginx/html
WORKDIR /usr/share/nginx/html
COPY hello_docker.html .

CMD nginx -g 'daemon off;'
