#  Docker - Noob to intermediate

### What is Docker ?
> Docker is one of the tools that used the idea of the isolated resources to create a set of tools that allows applications to be packaged with all the dependencies installed and ran wherever wanted.

### What is a Docker container ?
> A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. Basically kind of like a artifact that can be passed around after creating.

### What is Docker hub ?
> It is a library where a lot of containers exist for downloading and direct use. Docker hub helps us download base containers instead of developing everything from scratch.

### What is a Docker image ?
> A Docker image is a file used to execute code in a Docker container. Docker images act as a set of instructions to build a Docker container, like a template. Docker images also act as the starting point when using Docker. An image is comparable to a snapshot in virtual machine (VM) environments.

### Difference between docker and VM
> Usually an operating system is built with two main layers `Kernal` and `Application layer`.This being the main difference between Docker and VM because as mentioned above VM is a virtual machine running an operating system consisting of both kernel and application layer but Docker only run the Application layer.

![Docker flow](/dockerflow.jpeg?raw=true "Dockerflow")

#Basic Docker commands
` docker pull [image_name]`

> This command pulls the corresponding image from a public repository (Docker Hub)

`docker run [image_name]`

> This command starts the container corresponding to the image name

`docker ps`

> This command lists all running containers in a system

`docker ps -a`

>This commands lists all running and dead containers in a system

`docker run -d [image_name]`

> This command runs the container even if the terminal is closed "-d" - detach mode

`docker run -p6000:6001`

>If multiple containers are running port binding is a very important work that needs to be done, so lets say there is an application running at port 3000 in my container and when i run the container on my host machine I obviously need to bind it with a port on my host machine so i can check out the application on the assigned port. Here "-p" port setting attribute and 6000 refers to host port and 6001 refers to container port. Also the multiple containers can run the containers at same port until or unless the host ports binded are different.

`docker start [id/name]`

> Starts the container corresponding to the id/name

`docker stop [id/name]`

> Stops the container corresponding to the id/name

`docker images`

> Lists all images in the host machine

`docker logs [id/name]`

>Produces the command logs of the container

`docker run -d -p6000:6001 -name [name_for_container] [image_name]`

>Assigns the name we wish to the container so referencing later can be easier

`docker exec -it [id/name] /bin/bash or /bin/sh`

>Takes us the inside the terminal of the container for debugging. "-it" stands for interactive terminal.

#### Docker network
> So to run multiple containers which needs to communicate with each other we can create a docker network where those containers can run like a bunch of containers in a private cloud. Docker itself creates a network everytime a container is started if there is no network created by the user.

`docker network ls`

> Lists all the docker networks - User created or auto created.

`docker network create [network_name]`

> Creates network with a particular name

`docker run -p27017:27017 -d --name [container_name] --net [network_name]`
> Runs the container in a mentioned network so the user can group all the containers for a single project.

#### Docker compose
> Docker Compose is a tool that was developed to help define and share multi-container applications. With Compose, we can create a YAML file to define the services and with a single command, can spin everything up or tear it all down.

`docker compose -f [file_name] up`
> Starts all the processes in the docker compose file.

`docker-compose -f [file_name] down`
> Stops all the processes in the docker compose file.

#### Creating our own image
> To create our own docker image, firstly we need to have a docker file consisting the set of the instructions the container should follow.


`docker build -t [image_name]:[tag] [path_to_docker_file]`
> Builds a image on our local machine with the help of docker file.

`docker rmi [image_name]`
> Removes the image from our local machine

#### Difference between dockerfile and docker-compose.yml
> The main difference is that, dockerfile is a set of instructions that the container should follow and docker-compose.yml consists instructions to spin or tear down multiple containers at a single shot .

![Dockerfile example](/Dockerfile_example.png?raw=true "Dockerfile example")

#### Persisting data with volumes
> Usually data that the containers store or contain is just stored in the virtual filesystem which gets erased everytime the containers stops or restarts. To avoid this issue we have three ways in which we can mount the memory volumes.

1.  Host volume

`docker run -v home/mount/data:/var/lib/mysql/data`
> This command mounts the container storage with a host volume which helps us retrieve data provided we know the location on the host machine.

2. Anonymous volume

`docker run -v /var/lib/mysql/data`
> Here the host location is taken care by the container itself, basically a folder gets generated in the host machine and the container gets mounted.

3. Named volumes ( production used method)

`docker run -v name:/var/lib/mysql/data`
> Any name reference can be given to the memory volume which makes the work easier to retrieve it later if needed.
