# Example

## Concepts
*  Basic Docker commands


## Container
### show running container
````
docker ps
````
### show all containers
````
docker ps -a
````
### remove all stopped containers
````
docker rm $(docker ps -aq)
````
## Images
### show avaliable images
````
docker images
````
### pull an image
````
docker pull busybox
````
### run a command
````
docker run busybox echo hello
````
### run an interactive shell
````
docker run -i -t busybox /bin/sh
````
## Container Lifecycle
### start
````
docker run -d busybox /bin/sh -c "while true; do echo Hello word; sleep 1; done"
````
### logs
````
docker logs <containerID>
````
### stop & start
````
docker kill / stop /start <containerID>
````
## Building custom Docker containers
### build dockerimage from dockerfile
````
docker build -t nodejs:helloworld .
````
### run image and expose to port 8080
````
docker run  -p 8080:8080 -d nodejs:helloworld
````

