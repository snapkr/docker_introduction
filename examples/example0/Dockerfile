FROM ubuntu:latest

RUN apt-get update
RUN apt-get install -y nodejs

ADD server.js .

EXPOSE 80

CMD ["/usr/bin/nodejs","/server.js"]