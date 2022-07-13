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

#Basic Docker commands
    docker pull [image_name]
> This command pulls the corresponding image from a public repository (Docker Hub)
    docker run [image_name]
> This command starts the container corresponding to the image name
