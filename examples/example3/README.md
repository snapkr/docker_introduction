# Example

## Concepts
*  Network


With Docker and container technologies in general you have the posibility of managing their network. So far we have shown how you can bind a local port to an internal one on your host machine e.g.:
````
docker run  -p 80:8080 -d nodejs:helloworld
````
But Docker offers more sophisticated options for managing networks than just binding ports. In this section we will discover on of those options and show you how you can create virtual networks and later spin up an application that functions over multiple networks.

### Create Network
First we have to create a virtual network..
````
docker network create backend-network
````
..before we can connect an docker container by simply using the `--net` flag.
````
docker run -d --name=redis --net=backend-network redis
````


### Network Communication

Docker networks behave like traditional networks where containers can be attached/detached.

On the network the containers can communicate via an Embedded DNS Server in Docker. This DNS server is assigned to all containers via the IP 127.0.0.11 and set in the resolv.conf file.
````
docker run --net=backend-network alpine cat /etc/resolv.conf
````
Also when a container attempts to access another container via a host name, such as Redis, the DNS server will return the IP address of the correct container. In this case, the fully qualified name of Redis will be redis.backend-network. 
````
docker run --net=backend-network alpine ping -c3 redis
````


### Connect Multiple Containers

Now lets do some copy&paste work and spin up an application consisting of multiple containers and two neworks. The architecture will look as follows with the `voting-app` and `results-app` being part of the `frontend-network` and `backend-network` and the remaining containers only to the `backend-network`.
![architecture](architecture.png)
````
docker network create frontend-network
docker run -d --name=vote -p 5000:80 --net=frontend-network caylent/example-voting-app:vote
docker network create backend-network
docker network connect backend-network vote
docker run -d --name=redis --net=backend-network redis:alpine
docker run -d --name=db --net=backend-network postgres:9.4
docker run -d --name=result -p 5001:80  --net=frontend-network caylent/example-voting-app:result
docker run -d --name=worker --net=backend-network caylent/example-voting-app:worker
curl $(curl ipinfo.io/ip):5000 # vote app
curl $(curl ipinfo.io/ip):5001 # results app
````
You may notice that both frontend containers are also bound to the host network so we can see the web content. 

Otherwise we now have an functioning application in two networks and consisting of 5 containers.  Setting up an application like this is quite tedious which is why you will see a better way of doing the same task with less repetitiveness when doing operational tasks on such application. But first let us cover some more basics.

### Create Aliases

Usually a container is only reachable on an docker network via the assigned ip and name, if you wish to add a different name or need to add the same service twice you may use `aliases`
````
docker network create frontend-network2
docker network connect --alias db frontend-network2 redis
docker run --net=frontend-network2 alpine ping -c3 db
````


### Display Networks And Disconnect Containers

If you have mingled for some time with docker networks you may want to know how many networks you have and what is connected to those networks. Have a look at those commands and ingest their output.
````
docker network ls
docker network inspect frontend-network

````
Now remove all the containers and networks you have created during this example.
````
docker network disconnect <network name> <container name>
docker network rm <network name>
````
