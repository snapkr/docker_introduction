# Example

## Concepts
*  Docker compose

In this example we will execute an multi-container application using `docker compose`.

````
git clone `https://github.com/dockersamples/example-voting-app`
cd example-voting-app
# start the application
docker-compose up
````
The application will be running at the following endpoint,
````
 echo "http://$(docker-machine ip):5000/"
````
and the results will be shown at:
````
 echo "http://$(docker-machine ip):5000/"
````
