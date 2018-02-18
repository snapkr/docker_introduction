FROM ubuntu:latest

RUN apt-get update
RUN apt-get install -y nodejs

ADD server.js .

EXPOSE 8080

CMD ["/usr/bin/nodejs","/server.js"]