# Example

## Concepts
*  Volumes
*  Arguments
*  Environment variables


## Commands

In this section we have our files in a seperate directory `./data/` which we will mount into a Dockercontainer. As opposed to `example 1` we won`t build a Dockerimage via a Dockerfile but rather use an Dockerimage straight from `hub.docker.com`.

````
docker search nginx
docker run -p -v data:/data nginx
curl
````

