FROM nginx
MAINTAINER nutanix@gmail.com 

EXPOSE 80

VOLUME /usr/share/nginx/html
WORKDIR /usr/share/nginx/html
COPY hello_docker.html /usr/share/nginx/html/index.html

CMD nginx -g 'daemon off;'
