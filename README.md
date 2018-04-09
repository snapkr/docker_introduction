
## Setup Docker Toolbox

### Requirements:
*  Docker Toolbox (Includes Docker, Virtualbox and git) https://docs.docker.com/toolbox/toolbox_install_windows/
*  Code Editor e.g. VS Code https://code.visualstudio.com/

### Setup:

Start `Docker Quickstart Terminal`.

> Note: If this does not work do the following. Start `Git Bash` and execute the following script `C:\Program Files\Docker Toolbox\start.sh`. The latter will setup docker and connect your Docker client with the Docker server, which runs in an virtual machine on VirtualBox.

For retreiving the ip of the boot2docker VM execute the following:
````
docker-machine ip
````

Verify that Docker is setup correctly by typing `docker version` after which you should see something similar to this:
```
$ docker version
Client:
 Version:       18.01.0-ce
 API version:   1.35
 Go version:    go1.9.2
 Git commit:    03596f51b1
 Built: Thu Jan 11 22:29:41 2018
 OS/Arch:       windows/amd64
 Experimental:  false
 Orchestrator:  swarm

Server:
 Engine:
  Version:      18.01.0-ce
  API version:  1.35 (minimum version 1.12)
  Go version:   go1.9.2
  Git commit:   03596f5
  Built:        Wed Jan 10 20:13:12 2018
  OS/Arch:      linux/amd64
  Experimental: false
```

After this move into a directory of your choice where we will keep all relavant files for the following activites.
For this activity we have to download two git projects from GitHub.

````
git clone https://github.com/snapkr/docker_introduction.git
git clone https://github.com/dockersamples/example-voting-app.git
$ cd docker_introduction/
````
