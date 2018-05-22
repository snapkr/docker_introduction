# Example

## Concepts
*  Docker Compose

In this example we will be using `docker compose`.
Docker Compose is a tool for defining and running multi-container Docker applications.

````
git clone https://github.com/dockersamples/example-voting-app
cd example-voting-app
````

Now have a look at the `docker-compose.yml` file and compare what you see to what you have done during the last example. Otherwise you may execute this file see what is does for you.

````
# start the application
docker-compose up
# docker-compose will now download missing images and configure docker up until runtime.
````

The application can be reachd at the following endpoint,
````
curl $(curl ipinfo.io/ip):5000/"
````
and the results will be shown at:
````
curl $(curl ipinfo.io/ip):5001/"
````
