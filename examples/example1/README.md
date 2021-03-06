# Example

## Concepts
*  Dockerfile
*  Basic Docker commands
*  Tags

## Commands

First take a look at the Dockerfile to get a feeling for what it does.

Then build a dockerimage from our dockerfile. The `-t` parameter defines a human friendly name and a tag.
````
docker build -t webserver:v1 .
````

After you have build the docker image you should be able to see your just build dockerimage in your local docker repository.
Type the following command listing local docker images.
````
docker images
````
Now start this dockerimage in detached mode and let it server traffic  to `0.0.0.0:5080` and curl afterwards that exact endpoint to verify that our setup works correctly.
````
docker run -d -p 5080:80 webserver:v1
curl $(curl ipinfo.io/ip):5080
````
Now we have one working docker instance of nginx serving a static html website.


We could now modify the message in our `index.html` file and rebuild a second dockerimage with the same name but different tag.
Do so as you wish and rebuild the dockerfile and spin it up to serve http traffic on `localhost:5081`.
````
docker build -t webserver:v2 .
docker run -d -p 5081:80 webserver:v2
docker ps
````

The last command listed all running docker instances on your machine. Also if you curl both setup endpoints you will discover that the first docker instance running the image `webserver:v1` still shows our earlier version of the `index.html` file as it is baked into that image.

````
curl $(curl ipinfo.io/ip):5080
curl $(curl ipinfo.io/ip):5081
````


