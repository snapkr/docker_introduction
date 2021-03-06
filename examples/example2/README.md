# Example

## Concepts
*  Volumes
*  Arguments
*  Environment variables


## Commands

In this section we have our files in a seperate directory `./data/` which we will mount into a Dockercontainer. As opposed to `example 1` we won't build a Dockerimage via a Dockerfile but rather use an Dockerimage straight from `hub.docker.com`.

````
docker search nginx
docker run -d -p 5082:80 -v /$(pwd)/data:/usr/share/nginx/html nginx
curl $(curl ipinfo.io/ip):5082
````
You will see that the respone equals the content of the `./data/index.html` file. Also if you edit the file locally and save the file the response will change since that file is mounted as an volume into our docker container.
